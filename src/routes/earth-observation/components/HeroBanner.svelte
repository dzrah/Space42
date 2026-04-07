<script>
	import Container from '../../components/Container.svelte';
</script>

<svelte:head>
	<link rel="preload" as="image" href="/foresight-sky.webp" fetchpriority="high" />
</svelte:head>

<div
	class="relative w-full bg-cover bg-center bg-no-repeat min-h-64 lg:min-h-96 flex items-end"
	style="background-image: url('/foresight-sky.webp')"
>
	<div class="absolute inset-0 bg-[#0a0e2e]/60"></div>
	<Container class="relative z-10 py-16 lg:py-24">
		<h1
			class="font-antarctica font-semibold text-white text-3xl sm:text-4xl lg:text-5xl uppercase tracking-wide mb-4"
		>
			Earth Observation
		</h1>
		<p class="font-antarctica font-light text-white/80 text-base lg:text-lg">
			Understanding the planet through sovereign space infrastructure
		</p>
	</Container>
</div>
