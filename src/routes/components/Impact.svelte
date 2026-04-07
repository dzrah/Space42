<script lang="ts">
	import Container from './Container.svelte';
	import { fade } from 'svelte/transition';

	const slides = [
		{
			title: 'GOVERNMENTS AND NATIONAL SYSTEMS',
			tagline: 'Strengthening sovereign capability through space infrastructure, intelligent systems, and Earth observation.',
			image: '/img-1.webp',
			paragraphs: [
				'Governments help protect borders through managing critical infrastructure, responding to emergencies, and planning long-term national development. At a time when national security, environmental pressures, and economic priorities are increasingly interconnected, governments require trusted, sovereign access to intelligence, connectivity, and infrastructure that operates beyond the limits of terrestrial networks.',
				'By combining secure communications with advanced Earth observation and geospatial intelligence, Space42 enables continuous visibility, informed decision-making, and coordinated action across national systems.'
			]
		},
		{
			title: 'TELECOMMUNICATIONS SECTOR',
			tagline: 'Extending network reach through integrated satellite and terrestrial connectivity.',
			image: '/Telecommunications (woman).webp',
			paragraphs: [
				'Telecommunications providers face increasing pressure to expand coverage, improve network resilience, and deliver new services in markets where terrestrial infrastructure alone cannot meet demand.',
				'Mobile operators are now preparing for the next evolution of connectivity, where satellite and terrestrial networks operate seamlessly together to support direct-to-device services, IoT connectivity, and truly global coverage.'
			]
		},
		{
			title: 'ENERGY SECTOR',
			tagline: 'Strengthening operational resilience across critical energy infrastructure.',
			image: '/Energy (oil rig).webp',
			paragraphs: [
				'Energy operations span some of the most complex and remote environments on Earth. Offshore platforms, pipelines, refineries, and exploration sites operate across vast territories where terrestrial connectivity is limited, and real-time visibility is critical.',
				'To operate effectively at this scale, energy operators require trusted infrastructure that provides continuous connectivity, reliable monitoring, and intelligent insights across their entire operational landscape.'
			]
		},
		{
			title: 'MARITIME SECTOR',
			tagline: 'Strengthening connectivity and awareness across global maritime operations.',
			image: '/Maritime (ship).webp',
			paragraphs: [
				'The maritime domain underpins global trade, energy supply, and national security. Maritime operators must navigate complex challenges, from ensuring crew safety and maintaining operational communications to monitoring maritime traffic, protecting critical infrastructure, and responding to environmental or security incidents at sea.'
			]
		},
		{
			title: 'ENTERPRISE SECTOR',
			tagline: 'Connecting operations and intelligence across global enterprise environments.',
			image: '/Enterprise (man).webp',
			paragraphs: [
				'Large enterprises operate across increasingly complex environments.',
				'From logistics networks and mining operations to infrastructure management and environmental monitoring, organisations must coordinate operations across vast territories where traditional infrastructure cannot always provide the visibility or connectivity required.'
			]
		}
	];

	let current = $state(0);

	function prev() {
		current = (current - 1 + slides.length) % slides.length;
	}

	function next() {
		current = (current + 1) % slides.length;
	}
</script>

<div class="relative overflow-hidden">
	<div class="absolute inset-0 bg-[url('/blue_dark.webp')] bg-cover bg-center"></div>

	<Container class="relative z-10 pt-12 pb-0 lg:pt-20 lg:pb-0">

		<!-- Section heading -->
		<h2 class="font-antarctica font-semibold text-white text-xl lg:text-2xl mb-2">
			Where Space42 delivers impact
		</h2>

		<!-- Fixed height wrapper prevents section from jumping between slides -->
		<div class="min-h-[520px] lg:min-h-[560px] flex flex-col">
		{#key current}
			<div in:fade={{ duration: 300 }} class="flex flex-col flex-1">
				<p class="font-antarctica font-bold text-white text-xs lg:text-sm tracking-widest mt-6 mb-1 uppercase">
					{slides[current].title}
				</p>
				<p class="font-antarctica font-light text-white text-sm lg:text-base mb-8">
					{slides[current].tagline}
				</p>

				<!-- Slider content — image column uses full section height to push image to bottom -->
				<div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-end flex-1">

					<!-- Left: image pinned to bottom edge, gets clipped cleanly -->
					<div class="relative flex items-end justify-center min-h-80 lg:min-h-96">
						<button
							onclick={prev}
							class="absolute left-0 top-1/2 -translate-y-1/2 z-10 text-white/50 hover:text-white transition-colors cursor-pointer"
							aria-label="Previous"
						>
							<svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
							</svg>
						</button>

						<img
				loading="lazy"
							src={slides[current].image}
							alt={slides[current].title}
							class="w-auto max-w-[75%] max-h-[420px] object-contain object-bottom self-end"
						/>

						<button
							onclick={next}
							class="absolute right-0 top-1/2 -translate-y-1/2 z-10 text-white/50 hover:text-white transition-colors cursor-pointer"
							aria-label="Next"
						>
							<svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
							</svg>
						</button>
					</div>

					<!-- Right: text -->
					<div class="flex flex-col gap-4 pb-12 lg:pb-20">
						{#each slides[current].paragraphs as para}
							<p class="font-antarctica font-light text-white/85 text-xs lg:text-sm leading-relaxed">
								{para}
							</p>
						{/each}

						<!-- Dots -->
						<div class="flex gap-2 mt-6">
							{#each slides as _, i}
								<button
									onclick={() => (current = i)}
									class="w-3 h-3 rounded-full cursor-pointer transition-colors {i === current ? 'bg-blue-300' : 'bg-blue-800'}"
									aria-label="Go to slide {i + 1}"
								></button>
							{/each}
						</div>
					</div>
				</div>
			</div>
		{/key}
		</div>

	</Container>
</div>
