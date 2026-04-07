<script>
	import Container from '../../components/Container.svelte';
	import Section from '../../components/Section.svelte';

	const cards = [
		{
			title: 'Digital Twin Integration',
			subtitle: 'Transforming geospatial data into operational intelligence',
			image: '/digital twin screen grab.webp',
			paragraphs: [
				"GIQ is Space42's advanced geospatial intelligence platform, designed to integrate satellite imagery, sensor data, and advanced AI analytics into a unified operational environment.",
				'While Foresight delivers continuous Earth observation, GIQ ingests SAR, optical, and multi-source data and applies AI-driven analytics to convert raw imagery into structured, actionable intelligence that can be used across missions, sectors, and decision environments.',
				'This removes the biggest barrier in geospatial workflows: the gap between data collection and usable insight. Through GIQ, organisations gain access to a unified platform that delivers timely, interpretable, and directly applicable intelligence, moving away from managing fragmented datasets, complex tools, and manual analysis processes.'
			]
		},
		{
			title: 'Autonomous Mobility Control Centre',
			subtitle: 'Secure access to geospatial data and analytics services',
			image: '/GIX screen grab.webp',
			paragraphs: [
				"GIX is Space42's secure, operational geospatial intelligence platform, designed for environments where intelligence must be produced, managed, and acted on within controlled, mission-critical settings.",
				'While GIQ enables broad access to geospatial intelligence at scale, GIX is built for organisations that require end-to-end control over the intelligence lifecycle, from tasking and collection through to analysis and decision-making. It is designed to operate within sovereign, restricted, or high-security environments, where data sensitivity, workflow control, and operational assurance are critical.',
				'This means intelligence is generated faster, as well as being managed, secured, and operationalised within their own environment, without dependency on external systems or fragmented workflows.'
			]
		}
	];
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container class="pb-12 lg:pb-20">
		<h2 class="font-antarctica font-semibold text-[#121a6b] text-xl lg:text-2xl mb-6">
			Fleet operations and control
		</h2>

		<div class="grid grid-cols-1 md:grid-cols-2 gap-4 lg:gap-6">
			{#each cards as card}
				<div class="bg-white rounded-sm p-5 sm:p-8 flex flex-col gap-4">
					<!-- Title -->
					<h3
						class="font-antarctica font-semibold text-[#121a6b] text-2xl lg:text-3xl uppercase leading-tight"
					>
						{card.title}
					</h3>
					<!-- Subtitle -->
					<p class="font-antarctica font-light text-gray-600 text-sm leading-relaxed">
						{card.subtitle}
					</p>
					<!-- Image -->
					<img
				loading="lazy" src={card.image} alt={card.title} class="w-full h-56 lg:h-72 object-cover" />
					<!-- Paragraphs -->
					{#each card.paragraphs as para}
						<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
							{para}
						</p>
					{/each}
				</div>
			{/each}
		</div>
	</Container>
</Section>
