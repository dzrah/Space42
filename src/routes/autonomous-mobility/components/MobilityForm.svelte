<script lang="ts">
	import { onMount } from 'svelte';
	import Section from '../../components/Section.svelte';
	import Container from '../../components/Container.svelte';

	onMount(() => {
		if (document.querySelector('script[src*="FormLoader"]')) {
			fixFormWidth();
			return;
		}
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
		const wrapper = document.querySelector('.am-dynamics-form-wrapper');
		if (!wrapper) return;

		const form = wrapper.querySelector('.marketingForm');
		if (form) (form as HTMLElement).style.fontFamily = "'Antartica', sans-serif";

		wrapper.querySelectorAll<HTMLElement>('input, textarea, select').forEach((el) => {
			el.style.cssText = `
				width: 100% !important; max-width: 100% !important; min-width: 100% !important;
				flex: none !important; flex-basis: 100% !important; display: block !important;
				padding: 14px 16px !important; background-color: #ffffff !important;
				border: 1px solid #e5e7eb !important; border-radius: 8px !important;
				font-size: 16px !important; font-family: 'Antartica', sans-serif !important;
				color: #374151 !important; box-sizing: border-box !important; height: auto !important;
			`;
		});

		wrapper.querySelectorAll<HTMLElement>('textarea').forEach((el) => {
			el.style.cssText += 'min-height: 120px !important; resize: vertical !important;';
		});

		wrapper
			.querySelectorAll<HTMLElement>(
				'.textFormFieldBlock, .optionSetFormFieldBlock, .phoneFormFieldBlock, .lookupFormFieldBlock, .dateTimeFormFieldBlock, .multiOptionSetFormFieldBlock, .twoOptionFormFieldBlock'
			)
			.forEach((el) => {
				if (el.getAttribute('data-hide') === 'hide') {
					el.style.cssText = 'display: none !important;';
					return;
				}
				el.style.cssText = `
					display: block !important; width: 100% !important; max-width: 100% !important;
					padding: 0 !important; margin: 0 !important; box-sizing: border-box !important;
				`;
			});

		wrapper.querySelectorAll<HTMLElement>('label').forEach((el) => {
			el.style.cssText = `
				display: block !important; width: 100% !important; flex: none !important;
				margin-bottom: 8px !important; font-size: 14px !important; font-weight: 600 !important;
				font-family: 'Antartica', sans-serif !important; color: #374151 !important;
			`;
		});

		wrapper.querySelectorAll<HTMLElement>('[data-editorblocktype="Text"]').forEach((el) => {
			el.style.display = 'none';
		});

		wrapper.querySelectorAll<HTMLElement>('.submitButton').forEach((el) => {
			el.style.cssText = `
				background-color: #1e40af !important; color: #ffffff !important;
				font-weight: 600 !important; font-size: 14px !important;
				font-family: 'Antartica', sans-serif !important; padding: 14px 48px !important;
				border: none !important; border-radius: 8px !important; cursor: pointer !important;
			`;
		});

		wrapper.querySelectorAll<HTMLElement>('.submitButtonWrapper').forEach((el) => {
			el.style.cssText = `padding: 20px 0 !important; text-align: right !important; width: 100% !important;`;
		});

		wrapper.querySelectorAll<HTMLElement>('.inner, .columnContainer, th, td').forEach((el) => {
			el.style.padding = '0';
		});
	}
</script>

<Section id="contact" bgClass="bg-[#f0f1f7]">
	<Container>
		<div class="flex flex-col md:flex-row gap-8 lg:gap-12 py-16 lg:py-24 items-start">
			<!-- Left -->
			<div class="w-full md:w-[35%] shrink-0">
				<h2
					class="font-antarctica font-semibold text-[#121a6b] text-xl sm:text-2xl leading-snug mb-4"
				>
					Enable autonomous operations
				</h2>
				<p class="font-antarctica font-light text-gray-600 text-sm leading-relaxed mb-6">
					Tell us about your use case and environment. Our team will help you deploy safe, scalable
					autonomous mobility solutions.
				</p>
				<p class="font-antarctica font-light text-gray-500 text-xs">* Mandatory Field</p>
			</div>
			<!-- Right: Dynamics form -->
			<div class="w-full md:w-[65%] min-w-0">
				<div class="am-dynamics-form-wrapper">
					<!-- TODO: Replace with Autonomous Mobility form ID -->
					<div
						data-form-id="f8b0e036-9a2d-f111-8341-7ced8d579011"
						data-form-api-url="https://public-uae.mkt.dynamics.com/api/v1.0/orgs/b0843b43-2e40-ee11-94d3-6045bd6a6257/landingpageforms"
						data-cached-form-url="https://assets-uae.mkt.dynamics.com/b0843b43-2e40-ee11-94d3-6045bd6a6257/digitalassets/forms/f8b0e036-9a2d-f111-8341-7ced8d579011"
					></div>
				</div>
			</div>
		</div>
	</Container>
</Section>
