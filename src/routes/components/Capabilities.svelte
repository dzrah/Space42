<script>
	import Container from './Container.svelte';
	import Section from './Section.svelte';

	const cards = [
		{
			title: 'SECURE\nCONNECTIVITY',
			description: 'Reliable communications on Earth.',
			image: '/secure-connectivity-image.webp',
			href: '/secure-connectivity'
		},
		{
			title: 'EARTH\nOBSERVATION',
			description: 'Understanding the planet through sovereign space infrastructure.',
			image: '/Asset 3@4x-100.webp',
			href: '/earth-observation'
		},
		{
			title: 'GEOSPATIAL\nINTELLIGENCE',
			description: 'Turning space data into actionable insight.',
			image: '/jQxknZ@4x-100.webp',
			href: '/earth-observation#giq'
		},
		{
			title: 'INTEGRATED\nSYSTEMS',
			description:
				'Combining connectivity, observation and intelligence into autonomous mobility offering.',
			image: '/BuAODU@4x-100.webp',
			href: '/autonomous-mobility'
		}
	];
</script>

<Section id="solutions" class="relative overflow-hidden scroll-mt-24" bgClass="bg-transparent">
	<!-- Gray top (title area) -->
	<div class="absolute inset-x-0 top-0 h-[20%] bg-[#f0f1f7] -z-10"></div>
	<!-- Dark blue middle (cards area) -->
	<div
		class="absolute inset-x-0 top-[20%] bottom-0 bg-[url('/blue_dark.webp')] bg-cover bg-center -z-10"
	></div>

	<Container class="py-12 lg:py-20">
		<h2 class="font-antarctica font-semibold text-[#121a6b] text-xl lg:text-2xl mb-8 lg:mb-10">
			Many capabilities, one system
		</h2>

		<div class="grid grid-cols-1 sm:grid-cols-2 gap-4 lg:gap-6">
			{#each cards as card}
			<svelte:element
				this={card.href ? 'a' : 'div'}
				href={card.href || undefined}
				class="group bg-white flex flex-col overflow-hidden rounded-sm cursor-pointer"
			>
					<div class="p-6 pb-4">
						<h3
							class="font-antarctica font-semibold text-[#121a6b] text-xl lg:text-2xl leading-tight whitespace-pre-line"
						>
							{card.title}
						</h3>
						<p class="font-antarctica font-light text-sm text-gray-600 mt-2 leading-relaxed">
							{card.description}
						</p>
					</div>
					<div class="mt-auto w-full px-5 pb-4">
						<img
				loading="lazy" src={card.image} alt={card.title} class="w-full h-44 sm:h-56 lg:h-80 object-cover block" />
					</div>
					<!-- Animated bar -->
					<div class="relative mx-5 mb-4 h-[0.3rem] bg-[#9bd8ff] overflow-hidden">
						<div
							class="absolute inset-0 bg-[#121a6b] origin-left scale-x-0 group-hover:scale-x-100 transition-transform duration-500 ease-out"
						></div>
					</div>
			</svelte:element>
			{/each}
		</div>
	</Container>
</Section>
