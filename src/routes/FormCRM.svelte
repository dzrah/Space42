<script>
	import { onMount } from 'svelte';
	import Section from './components/Section.svelte';
	import Container from './components/Container.svelte';

	onMount(() => {
		const script = document.createElement('script');
		script.src =
			'https://cxppusa1formui01cdnsa01-endpoint.azureedge.net/uae/FormLoader/FormLoader.bundle.js';
		script.onload = () => {
			setTimeout(fixFormWidth, 500);
			setTimeout(fixFormWidth, 1000);
			setTimeout(fixFormWidth, 2000);
			setTimeout(fixFormWidth, 3500);
		};
		document.body.appendChild(script);
	});

	function fixFormWidth() {
		const wrapper = document.querySelector('.dynamics-form-wrapper');
		if (!wrapper) return;

		// Apply font to entire form
		const form = wrapper.querySelector('.marketingForm');
		if (form) {
			form.style.fontFamily = "'Antartica', sans-serif";
		}

		// Fix inputs - THE KEY IS flex: none !important in the inline style
		wrapper.querySelectorAll('input, textarea, select').forEach((el) => {
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

		// Fix textareas specifically
		wrapper.querySelectorAll('textarea').forEach((el) => {
			el.style.cssText += `
				min-height: 120px !important;
				resize: vertical !important;
			`;
		});

		// Fix ALL field block types - change from flex to block (but keep hidden fields hidden)
		wrapper
			.querySelectorAll(
				'.textFormFieldBlock, .optionSetFormFieldBlock, .phoneFormFieldBlock, .lookupFormFieldBlock, .dateTimeFormFieldBlock, .multiOptionSetFormFieldBlock, .twoOptionFormFieldBlock'
			)
			.forEach((el) => {
				// Skip fields that should be hidden
				if (el.getAttribute('data-hide') === 'hide') {
					el.style.cssText = 'display: none !important;';
					return;
				}

				el.style.cssText = `
					display: block !important;
					width: 100% !important;
					max-width: 100% !important;
					padding: 0px 0 !important;
					margin: 0 !important;
					box-sizing: border-box !important;
					flex-direction: unset !important;
					gap: unset !important;
				`;
			});

		// Fix ALL labels
		wrapper.querySelectorAll('label').forEach((el) => {
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
		});

		// Hide Dynamics headings
		wrapper.querySelectorAll('[data-editorblocktype="Text"]').forEach((el) => {
			el.style.display = 'none';
		});

		// Fix submit button
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

		wrapper.querySelectorAll('.submitButtonWrapper').forEach((el) => {
			el.style.cssText = `
				padding: 20px 0 !important;
				text-align: right !important;
				width: 100% !important;
			`;
		});

		// Fix any nested containers that might have padding
		wrapper.querySelectorAll('.inner, .columnContainer, th, td').forEach((el) => {
			el.style.padding = '0';
		});
	}
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container>
		<div class="form-section-wrapper">
			<!-- Left side: Text content -->
			<div class="form-text-side">
				<h2 class="form-title">Connect with Space42</h2>
				<p class="form-subtitle">
					Whether you’re exploring secure connectivity, geospatial intelligence, or integrated
					solutions, share your requirements and we’ll connect you with the right team.
				</p>
				<p class="form-mandatory">* Mandatory Field</p>
			</div>

			<!-- Right side: Dynamics Form -->
			<div id="contact"></div>
			<div class="form-container-side">
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
