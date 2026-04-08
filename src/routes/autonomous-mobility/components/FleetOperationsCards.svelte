<script>
	import Container from '../../components/Container.svelte';
	import Section from '../../components/Section.svelte';

	const cards = [
		{
			title: 'Digital Twin Integration',
			subtitle: 'Transforming geospatial data into operational intelligence',
			image: '/digital twin screen grab.webp',
			paragraphs: [
				'Space42’s Digital Twin platform creates dynamic, real-time representations of physical environments, enabling organisations to simulate, predict, and optimise outcomes before actions are taken in the real world.',
				'While GIQ provides intelligence on what is happening, the Digital Twin layer, extends this capability by modelling what could happen next. It integrates continuous data inputs from Space42’s ecosystem, including Foresight SAR, multi-source Earth observation, and AI-driven analytics, to create a live, evolving operational environment.',
				'This drives decision making based on real-time context, forward-looking scenarios, and measurable outcomes, enabling more confident planning and execution.'
			]
		},
		{
			title: 'Autonomous Mobility Control Centre',
			subtitle:
				'The platform includes a centralized operations systems, allowing operators to monitor and manage autonomous fleets in real time.',
			image: '/GIX screen grab.webp',
			paragraphs: [
				'- Real-time vehicle monitoring',
				'- Route planning and fleet coordination',
				'- Incident response and safety supervision',
				'- Operational analytics'
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
						loading="lazy"
						src={card.image}
						alt={card.title}
						class="w-full h-56 lg:h-72 object-cover"
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
