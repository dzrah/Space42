<script>
	import { onMount } from 'svelte';
	import Section from './components/Section.svelte';
	import Container from './components/Container.svelte';

	const SCRIPT_SRC =
		'https://cxppusa1formui01cdnsa01-endpoint.azureedge.net/uae/FormLoader/FormLoader.bundle.js';

	onMount(() => {
		const wrapper = document.querySelector('.dynamics-form-wrapper');
		if (!wrapper) return;

		// Re-run styling whenever Dynamics mutates the DOM inside the wrapper
		const observer = new MutationObserver(() => fixFormWidth(wrapper));
		observer.observe(wrapper, { childList: true, subtree: true });

		// Load the Dynamics FormLoader once (guard against duplicates on HMR/remount)
		if (!document.querySelector(`script[src="${SCRIPT_SRC}"]`)) {
			const script = document.createElement('script');
			script.src = SCRIPT_SRC;
			script.onerror = () => console.error('Dynamics FormLoader failed to load');
			document.body.appendChild(script);
		} else {
			// Already loaded — style whatever is there now
			fixFormWidth(wrapper);
		}
		``;

		return () => observer.disconnect();
	});

	function fixFormWidth(wrapper) {
		if (!wrapper) return;

		// Font on the whole form
		const form = wrapper.querySelector('.marketingForm');
		if (form) form.style.fontFamily = "'Antartica', sans-serif";

		// 1. Text inputs / textareas / selects — full width (EXCLUDE checkbox & radio)
		wrapper
			.querySelectorAll('input:not([type="checkbox"]):not([type="radio"]), textarea, select')
			.forEach((el) => {
				el.style.cssText = `
          width: 100% !important;
          max-width: 100% !important;
          min-width: 100% !important;
          flex: none !important;
          flex-basis: 100% !important;
          flex-grow: 0 !important;
          flex-shrink: 0 !important;
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
        `;
			});

		// 2. Textareas — taller + resizable
		wrapper.querySelectorAll('textarea').forEach((el) => {
			el.style.minHeight = '120px';
			el.style.resize = 'vertical';
		});

		// 3. Checkboxes & radios — keep small and inline
		wrapper.querySelectorAll('input[type="checkbox"], input[type="radio"]').forEach((el) => {
			el.style.cssText = `
        width: 18px !important;
        height: 18px !important;
        min-width: 18px !important;
        max-width: 18px !important;
        margin: 0 10px 0 0 !important;
        padding: 0 !important;
        flex: none !important;
        display: inline-block !important;
        vertical-align: middle !important;
        accent-color: #1e40af !important;
        cursor: pointer !important;
      `;
		});

		// 4. Each option row in multi-option set → flex row
		wrapper
			.querySelectorAll(
				'.multiOptionSetFormFieldBlock input[type="checkbox"], .multiOptionSetFormFieldBlock input[type="radio"]'
			)
			.forEach((box) => {
				const row = box.parentElement;
				if (row) {
					row.style.cssText = `
            display: flex !important;
            align-items: center !important;
            gap: 10px !important;
            padding: 6px 0 !important;
            width: 100% !important;
          `;
				}
			});

		// 5. Wrap the options container in a bordered box to match inputs
		wrapper.querySelectorAll('.multiOptionSetFormFieldBlock').forEach((block) => {
			if (block.getAttribute('data-hide') === 'hide') return;

			const firstBox = block.querySelector('input[type="checkbox"], input[type="radio"]');
			if (!firstBox) return;

			const row = firstBox.closest('div');
			const optionsContainer = row?.parentElement;

			if (optionsContainer && optionsContainer !== block && !optionsContainer.matches('label')) {
				optionsContainer.style.cssText = `
          background-color: #ffffff !important;
          border: 1px solid #e5e7eb !important;
          border-radius: 8px !important;
          padding: 8px 16px !important;
          width: 100% !important;
          box-sizing: border-box !important;
        `;
			}
		});

		// 6. Field block layout (skip hidden)
		wrapper
			.querySelectorAll(
				'.textFormFieldBlock, .optionSetFormFieldBlock, .phoneFormFieldBlock, .lookupFormFieldBlock, .dateTimeFormFieldBlock, .multiOptionSetFormFieldBlock, .twoOptionFormFieldBlock'
			)
			.forEach((el) => {
				if (el.getAttribute('data-hide') === 'hide') {
					el.style.cssText = 'display: none !important;';
					return;
				}
				el.style.cssText = `
          display: block !important;
          width: 100% !important;
          max-width: 100% !important;
          padding: 0 0 16px !important;
          margin: 0 !important;
          box-sizing: border-box !important;
          flex-direction: unset !important;
          gap: unset !important;
        `;
			});

		// 7. Labels — field labels vs option labels behave differently
		wrapper.querySelectorAll('label').forEach((el) => {
			const target = el.htmlFor ? document.getElementById(el.htmlFor) : null;
			const isOptionLabel =
				(target && (target.type === 'checkbox' || target.type === 'radio')) ||
				el.parentElement?.querySelector('input[type="checkbox"], input[type="radio"]');

			if (isOptionLabel) {
				el.style.cssText = `
          display: inline-block !important;
          width: auto !important;
          flex: 1 !important;
          margin: 0 !important;
          font-size: 15px !important;
          font-weight: 400 !important;
          font-family: 'Antartica', sans-serif !important;
          color: #374151 !important;
          cursor: pointer !important;
          vertical-align: middle !important;
        `;
			} else {
				el.style.cssText = `
          display: block !important;
          width: 100% !important;
          flex: none !important;
          margin-bottom: 8px !important;
          font-size: 14px !important;
          font-weight: 600 !important;
          font-family: 'Antartica', sans-serif !important;
          color: #374151 !important;
        `;
			}
		});

		// 8. Hide Dynamics text/heading blocks
		wrapper.querySelectorAll('[data-editorblocktype="Text"]').forEach((el) => {
			el.style.display = 'none';
		});

		// 9. Submit button
		wrapper.querySelectorAll('.submitButton').forEach((el) => {
			el.style.cssText = `
        background-color: #1e40af !important;
        color: #ffffff !important;
        font-weight: 600 !important;
        font-size: 14px !important;
        font-family: 'Antartica', sans-serif !important;
        padding: 14px 48px !important;
        border: none !important;
        border-radius: 8px !important;
        cursor: pointer !important;
      `;
		});

		// 10. Submit button wrapper — right-aligned
		wrapper.querySelectorAll('.submitButtonWrapper').forEach((el) => {
			el.style.cssText = `
        padding: 20px 0 !important;
        text-align: right !important;
        width: 100% !important;
      `;
		});

		// 11. Strip padding from nested containers
		wrapper.querySelectorAll('.inner, .columnContainer, th, td').forEach((el) => {
			el.style.padding = '0';
		});
	}
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container>
		<div class="form-section-wrapper">
			<!-- Left: Text -->
			<div class="form-text-side">
				<h2 class="form-title">Connect with Space42</h2>
				<p class="form-subtitle">
					Whether you're exploring secure connectivity, geospatial intelligence, or integrated
					solutions, share your requirements and we'll connect you with the right team.
				</p>
				<p class="form-mandatory">* Mandatory Field</p>
			</div>

			<!-- Right: Dynamics Form (anchor moved inside) -->
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
</style>
