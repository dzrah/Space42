<script>
	import Container from '../../components/Container.svelte';
</script>

<svelte:head>
	<link rel="preload" as="image" href="/about-us-banner-darker.webp" fetchpriority="high" />
</svelte:head>

<div
	class="relative w-full min-h-[480px] md:min-h-[540px] lg:min-h-[600px] bg-cover bg-center flex items-center"
	style="background-image: url('/about-us-banner-darker.webp')"
>
	<Container class="relative z-10 py-16 lg:py-24">
		<div class="w-full md:w-3/4 lg:w-[65%] xl:w-[70%] flex flex-col gap-6 text-white">
			<h1
				class="font-antarctica font-semibold text-xl sm:text-2xl md:text-3xl lg:text-4xl xl:text-5xl leading-tight uppercase"
			>
				BEYOND HORIZONS
			</h1>
			<p class="font-antarctica font-light text-sm lg:text-base leading-relaxed">
				Space42 is the UAE-based AI-powered SpaceTech company that integrates satellite
				communications, geospatial analytics, and AI capabilities.
			</p>
			<p class="font-antarctica font-light text-sm lg:text-base leading-relaxed">
				By integrating satellites, data platforms, AI, and secure connectivity, Space42 creates a
				continuous flow from observation to insight, and from insight to action.
			</p>
			<p class="font-antarctica font-light text-sm lg:text-base leading-relaxed">
				This ensures that every orbit, every platform, and every byte of data serves a meaningful
				purpose.
			</p>
		</div>
	</Container>
</div>
