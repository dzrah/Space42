<script lang="ts">
	import Container from './Container.svelte';

	const slides = [
		{
			title: 'THURAYA-4',
			subtitle: 'Secure. Validated. Operational.',
			description:
				'All Thuraya legacy services. Voice, SMS, and packet data have moved from Thuraya-2 to Thuraya-4, now powering the next generation NEO product line.',
			bg: '/homepage-thutara-4-banner.webp',
			image: '/satellite.webp',
			href: '/secure-connectivity'
		},
		{
			title: 'FORESIGHT CONSTELATION',
			subtitle: 'Understanding the planet through sovereign space infrastructure.',
			description:
				"Foresight is Space42's sovereign SAR constellation, designed to deliver continuous, high-resolution Earth observation that directly informs critical decisions.",
			bg: '/foresight-sky.webp',
			image: '/foresight.webp',
			href: '/earth-observation'
		},
		{
			title: 'AUTONOMOUS MOBILITY',
			subtitle: 'A Space42 sectorial priority',
			description:
				'Autonomous mobility represents one of the most transformative shifts in infrastructure, logistics, and public services.',
			bg: '/autonomous-mobility-banner-with-car.webp',
			image: '',
			href: '/autonomous-mobility'
		}
	];

	let current = $state(0);
	let interval: ReturnType<typeof setInterval>;

	function goTo(index: number) {
		current = index;
		restartInterval();
	}

	function next() {
		current = (current + 1) % slides.length;
	}

	function restartInterval() {
		clearInterval(interval);
		interval = setInterval(next, 15000);
	}

	$effect(() => {
		interval = setInterval(next, 15000);
		return () => clearInterval(interval);
	});
</script>

<svelte:head>
	<link rel="preload" as="image" href="/homepage-thutara-4-banner.webp" fetchpriority="high" />
</svelte:head>

<!-- Fixed height hero wrapper — overflow-visible so satellite can bleed below -->
<div class="relative w-full h-[260px] sm:h-[300px] md:h-[340px] lg:h-[380px] xl:h-[420px] overflow-visible">
	<!-- Background images clipped separately -->
	<div class="absolute inset-0 overflow-hidden">
		{#each slides as slide, i}
			<img
				src={slide.bg}
				alt=""
				loading={i === 0 ? 'eager' : 'lazy'}
				fetchpriority={i === 0 ? 'high' : 'auto'}
				class="absolute inset-0 w-full h-full object-cover object-center transition-opacity duration-700 {i ===
				current
					? 'opacity-100'
					: 'opacity-0'}"
			/>
		{/each}
	</div>

	<!-- Slide content -->
	<Container class="relative z-10 h-full flex items-center justify-between">
		<!-- Left: text full width on mobile, 3/5 on md+ -->
		<div class="relative w-full md:w-3/5 h-full flex items-center">
			{#each slides as slide, i}
				<div
					class="absolute inset-0 flex flex-col justify-center gap-2 md:gap-3 pb-10 transition-opacity duration-500 {i ===
					current
						? 'opacity-100'
						: 'opacity-0 pointer-events-none'}"
				>
					<h1
						class="font-antarctica font-semibold text-lg sm:text-2xl md:text-3xl lg:text-4xl xl:text-5xl tracking-wide text-white leading-tight"
					>
						{slide.title}
					</h1>
					<p class="font-antarctica font-light text-xs sm:text-sm lg:text-base text-white">
						{slide.subtitle}
					</p>
					<p class="font-antarctica font-light text-xs lg:text-sm leading-relaxed text-white/80">
						{slide.description}
					</p>
				</div>
			{/each}

			<!-- Button stays fixed, outside the animated slides -->
			<a
				href={slides[current].href}
				class="absolute bottom-6 left-0 inline-block border border-white text-white px-5 py-2.5 text-sm font-light hover:bg-white hover:text-[#121a6b] transition-all duration-200"
			>
				Learn more
			</a>
		</div>

		<!-- Right: slide image — hidden on mobile, bleeds below on md+ -->
		<div class="hidden md:block relative w-2/5 h-full">
			{#each slides as slide, i}
				{#if slide.image}
					<img
						src={slide.image}
						alt={slide.title}
						loading="lazy"
						class="absolute bottom-0 right-0 translate-y-1/4 h-full w-auto object-contain transition-opacity duration-500 {i ===
						current
							? 'opacity-100'
							: 'opacity-0'}"
					/>
				{/if}
			{/each}
		</div>
	</Container>

	<!-- Dot navigation -->
	<div class="absolute bottom-4 left-1/2 -translate-x-1/2 z-20 flex gap-2">
		{#each slides as _, i}
			<button
				onclick={() => goTo(i)}
				class="w-2 h-2 rounded-full border border-white transition-all duration-300 cursor-pointer {i ===
				current
					? 'bg-white'
					: 'bg-transparent'}"
				aria-label="Go to slide {i + 1}"
			></button>
		{/each}
	</div>
</div>
