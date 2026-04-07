<script>
	import Container from '../../components/Container.svelte';
	import Section from '../../components/Section.svelte';

	const pillars = [
		{
			icon: '/Preferred partner for premium.svg',
			label: 'Preferred partner for premium geospatial data'
		},
		{
			icon: '/Global leader in geospatial intelligence AI platform and services.svg',
			label: 'Global leader in geospatial intelligence AI platform and services'
		},
		{
			icon: '/Secure connectivity.svg',
			label: 'Trusted leader in secure connectivity'
		},
		{
			icon: '/Global NTN leadership.svg',
			label: 'Global NTN leadership'
		},
		{
			icon: '/Sectorial_priority.svg',
			label: 'Sectorial priority'
		}
	];

	const programs = [
		{
			title: 'Foresight constellation',
			content: [
				{
					subtitle: '',
					text: 'A next-generation SAR satellite constellation delivering persistent, all-weather Earth observation to power national security, infrastructure monitoring, and environmental intelligence.'
				}
			]
		},
		{
			title: 'GIQ',
			content: [
				{
					subtitle: '',
					text: 'Satellite-enabled intelligence service platform powering real-time data collection and transforming Earth observation data into actionable insights through AI-driven analytics and interactive visualization.'
				},
				{
					subtitle: 'Map Africa Initiative',
					text: "A continental-scale initiative to create Africa's first living digital map, providing the geospatial foundation for economic development, infrastructure planning, and smarter decision-making."
				}
			]
		},
		{
			title: 'Thuraya-4 next-generation satellite connectivity',
			content: [
				{
					subtitle: '',
					text: 'Next-generation satellite, delivering reliable connectivity across regions and use cases. Thuraya-4 supports mobility, mission-critical communications, and digital inclusion.'
				},
				{
					subtitle: 'Al Yah 4 and 5',
					text: 'Two advanced sovereign communications satellites with best-in-class technology. They will provide secure, resilient, high-capacity connectivity for UAE government and strategic national missions.'
				}
			]
		},
		{
			title: 'Equatys',
			content: [
				{
					subtitle: '',
					text: 'Open, interoperable Non-Terrestrial Network (NTN), seamlessly extending terrestrial connectivity to standard smartphones and IoT devices via satellite; no hardware modification required.'
				}
			]
		},
		{
			title: 'Autonomous mobility venture with A2Z',
			content: [
				{
					subtitle: '',
					text: 'A strategic venture advancing full-stack autonomous mobility systems that integrate AI, geospatial intelligence, and real-world operations to transform transport and infrastructure.'
				}
			]
		}
	];
</script>

<Section class="relative overflow-hidden" bgClass="bg-transparent">
	<!-- Top: same image as StrategicPillars, flipped vertically to connect seamlessly -->
	<div class="absolute inset-x-0 top-0 h-[35%] -z-10 overflow-hidden">
		<div
			class="absolute inset-0 bg-cover bg-center bg-no-repeat"
			style="background-image: url('/pillars-banner-expanded-about-us-page.webp'); transform: scaleY(-1);"
		></div>
		<div class="absolute inset-0 bg-[#0a0e2e]/80"></div>
	</div>
	<!-- Gray bottom -->
	<div class="absolute inset-x-0 top-[35%] bottom-0 bg-[#f0f1f7] -z-10"></div>

	<Container class="py-12 lg:py-20">
		<!-- White card -->
		<div class="bg-white rounded-2xl p-5 sm:p-8 lg:p-12 shadow-sm">
			<!-- Title -->
			<h2
				class="font-antarctica font-semibold text-[#121a6b] text-lg sm:text-2xl md:text-3xl lg:text-3xl xl:text-4xl uppercase leading-tight mb-8 sm:mb-10"
			>
				Flagship programs as engines of impact
			</h2>

			<!-- Pillar icons + labels row -->
			<div class="grid grid-cols-3 sm:grid-cols-5 gap-8 mb-8 pb-8 border-b border-[#c3ebff]">
				{#each pillars as pillar, i}
					<div class="relative flex flex-col items-start">
						<img
				loading="lazy"
							src={pillar.icon}
							alt={pillar.label}
							class="w-10 h-10 sm:w-12 sm:h-12 object-contain object-left mb-3 sm:mb-5"
						/>
						<p class="font-antarctica font-semibold text-[#0a82dc] text-xs sm:text-sm leading-snug">
							{pillar.label}
						</p>
						{#if i < pillars.length - 1}
							<div
								class="hidden sm:block absolute top-5 -translate-y-1/2 -translate-x-1/2 z-10"
								style="left: calc(50% + 1rem)"
							>
								<div class="w-8 h-2 bg-[#f0f1f7] rounded-full"></div>
							</div>
						{/if}
					</div>
				{/each}
			</div>

			<!-- Programs grid -->
			<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-5 gap-8">
				{#each programs as program}
					<div class="flex flex-col gap-4">
						<p class="font-antarctica font-semibold text-[#121a6b] text-sm leading-snug">
							{program.title}
						</p>
						{#each program.content as block}
							<div class="flex flex-col gap-1">
								{#if block.subtitle}
									<p class="font-antarctica font-semibold text-[#121a6b] text-sm">
										{block.subtitle}
									</p>
								{/if}
								<p class="font-antarctica font-light text-gray-600 text-sm leading-relaxed">
									{block.text}
								</p>
							</div>
						{/each}
					</div>
				{/each}
			</div>
		</div>
	</Container>
</Section>
