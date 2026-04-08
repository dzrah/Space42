<script>
	import Container from '../../components/Container.svelte';
	import Section from '../../components/Section.svelte';

	const cards = [
		{
			id: 'giq',
			title: 'Geospatial Intelligence Platform (GIQ)',
			subtitle: 'Transforming geospatial data into operational intelligence',
			image: '/jQxknZ@4x-100.webp',
			paragraphs: [
				"GIQ is Space42's advanced geospatial intelligence platform, designed to integrate satellite imagery, sensor data, and advanced AI analytics into a unified operational environment.",
				'While Foresight delivers continuous Earth observation, GIQ ingests SAR, optical, and multi-source data and applies AI-driven analytics to convert raw imagery into structured, actionable intelligence that can be used across missions, sectors, and decision environments.',
				'This removes the biggest barrier in geospatial workflows: the gap between data collection and usable insight. Through GIQ, organisations gain access to a unified platform that delivers timely, interpretable, and directly applicable intelligence, moving away from managing fragmented datasets, complex tools, and manual analysis processes.'
			]
		},
		{
			title: 'GIX',
			subtitle: 'Secure access to geospatial data and analytics services',
			image: '/GIX screen grab.webp',
			paragraphs: [
				'GIX is Space42’s secure, operational geospatial intelligence platform, designed for environments where intelligence must be produced, managed, and acted on within controlled, mission-critical settings.',
				'While GIQ enables broad access to geospatial intelligence at scale, GIX is built for organisations that require end-to-end control over the intelligence lifecycle, from tasking and collection through to analysis and dissemination. It is designed to operate within sovereign, restricted, or high-security environments where data control and operational assurance are critical.',
				'Geospatial intelligence is generated, managed, secured, and operationalised within their own environment, without dependence on external systems or fragmented workflows.'
			]
		},
		{
			title: 'Geospatial Mapping',
			subtitle: 'From data to decision-grade environments',
			image: '/geospacial mapping.webp',
			paragraphs: [
				'Space42 delivers high-precision geospatial mapping that forms the foundation for planning, simulation, and operational decision-making.',
				"By combining satellite imagery, aerial data, and ground-based surveys, Space42 creates detailed, up-to-date representations of the physical world. Integrated with Space42's AI ecosystem, these mapping products feed directly into GIQ and GIX AI-driven analytics, enabling organisations to move from data-rich environments to intelligence-ready operational environments."
			]
		},
		{
			title: 'Digital Twin',
			subtitle: 'Real-time simulation and monitoring of physical environments',
			image: '/digital twin screen grab.webp',
			paragraphs: [
				"Space42's Digital Twin platform creates dynamic, real-time representations of physical environments, enabling organisations to simulate, monitor, and model what could happen before actions are taken in the real world.",
				'Space42 provides uniquely powerful context. The Digital Twin layer extends this capability by modelling what could happen across the full Space42 ecosystem, including Foresight SAR, multi-source Earth observation, and AI-derived analytics, to build a complete operational environment.',
				'This drives decision-making based on real-time context, forward-looking scenarios, and continuous simulations enabling confident planning and execution.'
			]
		}
	];
</script>

<Section class="relative overflow-hidden" bgClass="bg-transparent">
	<div class="absolute inset-x-0 top-0 h-[10%] bg-[#f0f1f7] -z-10"></div>
	<div
		class="absolute inset-x-0 top-[10%] bottom-0 bg-[url('/blue_dark.webp')] bg-cover bg-center -z-10"
	></div>

	<Container class="pb-12 lg:pb-20">
		<div class="grid grid-cols-1 md:grid-cols-2 gap-4 lg:gap-6">
			{#each cards as card}
				<div
					id={card.id ?? undefined}
					class="bg-white rounded-sm p-5 sm:p-8 flex flex-col gap-4 scroll-mt-32"
				>
					<!-- Title -->
					<h2
						class="font-antarctica font-semibold text-[#121a6b] text-2xl lg:text-3xl uppercase leading-tight"
					>
						{card.title}
					</h2>
					<!-- Subtitle -->
					<p class="font-antarctica font-light text-gray-600 text-sm leading-relaxed">
						{card.subtitle}
					</p>
					<!-- Image -->
					<img
						loading="lazy"
						src={card.image}
						alt={card.title}
						class="w-full h-40 sm:h-48 lg:h-72 object-cover"
					/>
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
