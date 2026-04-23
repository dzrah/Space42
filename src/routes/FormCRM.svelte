<script>
	import { onMount } from 'svelte';
	import Section from './components/Section.svelte';
	import Container from './components/Container.svelte';

	const SCRIPT_SRC =
		'https://cxppusa1formui01cdnsa01-endpoint.azureedge.net/uae/FormLoader/FormLoader.bundle.js';

	onMount(() => {
		// Load the Dynamics FormLoader once (guard against duplicates on HMR/remount)
		if (!document.querySelector(`script[src="${SCRIPT_SRC}"]`)) {
			const script = document.createElement('script');
			script.src = SCRIPT_SRC;
			script.onerror = () => console.error('Dynamics FormLoader failed to load');
			document.body.appendChild(script);
		}

		// CSS handles styling. JS only handles things CSS can't do reliably:
		//   - Wrapping the checklist options container (needs DOM traversal)
		//   - Distinguishing option labels from field labels (needs sibling check)
		const wrapper = document.querySelector('.dynamics-form-wrapper');
		if (!wrapper) return;

		const applyStructuralFixes = () => {
			// Tag option labels so CSS can target them
			wrapper.querySelectorAll('input[type="checkbox"], input[type="radio"]').forEach((input) => {
				// Mark the input's row (its parent) for CSS
				const row = input.parentElement;
				if (row && !row.hasAttribute('data-option-row')) {
					row.setAttribute('data-option-row', 'true');
				}
				// Mark the label next to the checkbox as an option label
				const sibling = input.nextElementSibling;
				if (sibling && sibling.tagName === 'LABEL' && !sibling.hasAttribute('data-option-label')) {
					sibling.setAttribute('data-option-label', 'true');
				}
				const parentLabel = input.closest('label');
				if (parentLabel && !parentLabel.hasAttribute('data-option-label')) {
					parentLabel.setAttribute('data-option-label', 'true');
				}
			});

			// Tag the options container (parent of option rows) so CSS can wrap it in a box
			wrapper.querySelectorAll('.multiOptionSetFormFieldBlock').forEach((block) => {
				if (block.getAttribute('data-hide') === 'hide') return;
				const firstRow = block.querySelector('[data-option-row="true"]');
				const container = firstRow?.parentElement;
				if (container && container !== block && !container.hasAttribute('data-options-box')) {
					container.setAttribute('data-options-box', 'true');
				}
			});
		};

		// Run now, then re-run whenever Dynamics mutates the DOM
		applyStructuralFixes();
		const observer = new MutationObserver(applyStructuralFixes);
		observer.observe(wrapper, { childList: true, subtree: true });

		return () => observer.disconnect();
	});
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container>
		<div class="form-section-wrapper">
			<!-- Left: Text -->
			<div class="form-text-side">
				<h1 class="form-title">Connect with Space42</h1>
				<p class="form-subtitle">
					Whether you're exploring secure connectivity, geospatial intelligence, or integrated
					solutions, share your requirements and we'll connect you with the right team.
				</p>
				<p class="form-mandatory">* Mandatory Field</p>
			</div>

			<!-- Right: Dynamics Form -->
			<div id="contact" class="form-container-side">
				<div class="dynamics-form-wrapper">
					<div
						data-form-id="272aa958-972d-f111-8341-7ced8d579011"
						data-form-api-url="https://public-uae.mkt.dynamics.com/api/v1.0/orgs/b0843b43-2e40-ee11-94d3-6045bd6a6257/landingpageforms"
						data-cached-form-url="https://assets-uae.mkt.dynamics.com/b0843b43-2e40-ee11-94d3-6045bd6a6257/digitalassets/forms/272aa958-972d-f111-8341-7ced8d579011"
					></div>
				</div>
			</div>
		</div>
	</Container>
</Section>

<style>
	/* ===== Layout ===== */
	.form-section-wrapper {
		display: flex;
		flex-direction: column;
		width: 100%;
		gap: 2rem;
		padding: 3rem 0;
	}
	@media (min-width: 640px) {
		.form-section-wrapper {
			padding: 4.5rem 0;
		}
	}
	@media (min-width: 768px) {
		.form-section-wrapper {
			flex-direction: row;
			align-items: flex-start;
			gap: 3rem;
		}
	}

	.form-text-side {
		width: 100%;
		flex-shrink: 0;
	}
	@media (min-width: 768px) {
		.form-text-side {
			width: 35%;
			padding-right: 1rem;
		}
	}

	.form-title {
		color: #0e329b;
		font-weight: 600;
		font-size: 1.3rem;
		line-height: 1.3;
		margin-bottom: 1rem;
		text-align: center;
	}
	@media (min-width: 640px) {
		.form-title {
			font-size: 1.7rem;
			text-align: left;
		}
	}

	.form-subtitle {
		font-weight: 300;
		font-size: 1rem;
		color: #666666;
		margin-bottom: 2rem;
		text-align: center;
	}
	@media (min-width: 640px) {
		.form-subtitle {
			font-size: 1.2rem;
			text-align: left;
		}
	}

	.form-mandatory {
		font-weight: 300;
		font-size: 0.85rem;
		color: #666666;
		text-align: center;
	}
	@media (min-width: 640px) {
		.form-mandatory {
			text-align: left;
		}
	}

	.form-container-side {
		width: 100%;
		min-width: 0;
	}
	@media (min-width: 768px) {
		.form-container-side {
			width: 65%;
		}
	}

	.dynamics-form-wrapper {
		width: 100%;
	}

	/* ===== Dynamics form overrides =====
     :global is required because Svelte scopes styles by default,
     and Dynamics-injected DOM won't have Svelte's scoping hash. */

	:global(.dynamics-form-wrapper .marketingForm) {
		font-family: 'Antartica', sans-serif !important;
	}

	/* --- Text inputs, textareas, selects --- */
	:global(
		.dynamics-form-wrapper
			input:not([type='checkbox']):not([type='radio']):not([type='submit']):not([type='button'])
	),
	:global(.dynamics-form-wrapper textarea),
	:global(.dynamics-form-wrapper select) {
		width: 100% !important;
		max-width: 100% !important;
		min-width: 0 !important;
		flex: none !important;
		display: block !important;
		padding: 14px 16px !important;
		background-color: #ffffff !important;
		border: 1px solid #e5e7eb !important;
		border-radius: 8px !important;
		font-size: 16px !important;
		font-family: 'Antartica', sans-serif !important;
		color: #374151 !important;
		box-sizing: border-box !important;
		height: auto !important;
	}

	:global(.dynamics-form-wrapper textarea) {
		min-height: 120px !important;
		resize: vertical !important;
	}

	/* --- Checkboxes & radios --- */
	:global(.dynamics-form-wrapper input[type='checkbox']),
	:global(.dynamics-form-wrapper input[type='radio']) {
		width: 18px !important;
		height: 18px !important;
		min-width: 18px !important;
		max-width: 18px !important;
		flex: none !important;
		display: inline-block !important;
		margin: 0 10px 0 0 !important;
		padding: 0 !important;
		vertical-align: middle !important;
		accent-color: #1e40af !important;
		cursor: pointer !important;
	}

	/* --- Option rows (tagged by JS) --- */
	:global(.dynamics-form-wrapper [data-option-row='true']) {
		display: flex !important;
		align-items: center !important;
		gap: 10px !important;
		padding: 6px 0 !important;
		width: 100% !important;
		flex-direction: row !important;
	}

	/* --- Field block layout --- */
	:global(.dynamics-form-wrapper .textFormFieldBlock),
	:global(.dynamics-form-wrapper .optionSetFormFieldBlock),
	:global(.dynamics-form-wrapper .phoneFormFieldBlock),
	:global(.dynamics-form-wrapper .lookupFormFieldBlock),
	:global(.dynamics-form-wrapper .dateTimeFormFieldBlock),
	:global(.dynamics-form-wrapper .multiOptionSetFormFieldBlock),
	:global(.dynamics-form-wrapper .twoOptionFormFieldBlock) {
		display: block !important;
		width: 100% !important;
		max-width: 100% !important;
		padding: 0 0 16px !important;
		margin: 0 !important;
		box-sizing: border-box !important;
		flex-direction: unset !important;
		gap: unset !important;
	}

	:global(.dynamics-form-wrapper [data-hide='hide']) {
		display: none !important;
	}

	/* --- Field labels (default) --- */
	:global(.dynamics-form-wrapper label) {
		display: block !important;
		width: 100% !important;
		flex: none !important;
		margin-bottom: 8px !important;
		font-size: 14px !important;
		font-weight: 600 !important;
		font-family: 'Antartica', sans-serif !important;
		color: #374151 !important;
	}

	/* --- Option labels override field label rule --- */
	:global(.dynamics-form-wrapper label[data-option-label='true']) {
		display: inline-block !important;
		width: auto !important;
		flex: 1 !important;
		margin: 0 !important;
		font-size: 15px !important;
		font-weight: 400 !important;
		color: #374151 !important;
		cursor: pointer !important;
		vertical-align: middle !important;
	}

	/* --- Checklist container — bordered box (tagged by JS) --- */
	:global(.dynamics-form-wrapper [data-options-box='true']) {
		background-color: #ffffff !important;
		border: 1px solid #e5e7eb !important;
		border-radius: 8px !important;
		padding: 8px 16px !important;
		width: 100% !important;
		box-sizing: border-box !important;
	}

	/* --- Hide Dynamics rich-text blocks --- */
	:global(.dynamics-form-wrapper [data-editorblocktype='Text']) {
		display: none !important;
	}

	/* --- Submit button --- */
	:global(.dynamics-form-wrapper .submitButton) {
		background-color: #1e40af !important;
		color: #ffffff !important;
		font-weight: 600 !important;
		font-size: 14px !important;
		font-family: 'Antartica', sans-serif !important;
		padding: 14px 48px !important;
		border: none !important;
		border-radius: 8px !important;
		cursor: pointer !important;
	}

	:global(.dynamics-form-wrapper .submitButtonWrapper) {
		padding: 20px 0 !important;
		text-align: right !important;
		width: 100% !important;
	}

	/* --- Strip inherited padding from nested containers --- */
	:global(.dynamics-form-wrapper .inner),
	:global(.dynamics-form-wrapper .columnContainer),
	:global(.dynamics-form-wrapper th),
	:global(.dynamics-form-wrapper td) {
		padding: 0 !important;
	}
</style>
