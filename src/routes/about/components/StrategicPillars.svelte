<script>
	import Container from '../../components/Container.svelte';
</script>

<div
	class="relative w-full bg-cover bg-center bg-no-repeat"
	style="background-image: url('/pillars-banner-expanded-about-us-page.webp')"
>
	<!-- Dark overlay -->
	<div class="absolute inset-0 bg-[#0a0e2e]/80"></div>

	<Container class="relative z-10 py-16 lg:py-24">
		<!-- Title -->
		<h2
			class="font-antarctica font-semibold text-white text-xl sm:text-2xl md:text-3xl lg:text-4xl uppercase leading-tight mb-8"
		>
			Space42 is guided by four strategic pillars
		</h2>

		<!-- Intro text -->
		<div class="flex flex-col gap-3 mb-12 max-w-3xl">
			<p class="font-antarctica font-light text-white/80 text-sm leading-relaxed">
				At Space42, our strategy is anchored on four strategic pillars which guide every decision we make,
				from the satellites we build to the AI platforms we launch, ensuring a clear path from vision to measurable impact.
			</p>
		</div>

		<!-- 4 Pillars grid -->
		<div class="grid grid-cols-1 sm:grid-cols-2 mb-0">
			<!-- Pillar 1 -->
			<div class="border-b border-white/20 sm:border-r py-6 lg:py-8 sm:pr-6 lg:pr-8">
				<p class="font-antarctica font-semibold text-white text-sm mb-3">
					Preferred partner for premium geospatial data
				</p>
				<p class="font-antarctica font-light text-white/70 text-sm leading-relaxed">
					Build tier-1 sovereign multi-sensor Earth observation assets and capabilities
				</p>
			</div>
			<!-- Pillar 2 -->
			<div class="border-b border-white/20 py-6 lg:py-8 sm:pl-6 lg:pl-8">
				<p class="font-antarctica font-semibold text-white text-sm mb-3">
					Global leader in geospatial intelligence AI platform and services
				</p>
				<p class="font-antarctica font-light text-white/70 text-sm leading-relaxed">
					Deliver actionable insights to global customers
				</p>
			</div>
			<!-- Pillar 3 -->
			<div class="border-b border-white/20 sm:border-b-0 sm:border-r py-6 lg:py-8 sm:pr-6 lg:pr-8">
				<p class="font-antarctica font-semibold text-white text-sm mb-3">Global NTN leadership</p>
				<p class="font-antarctica font-light text-white/70 text-sm leading-relaxed">
					Lead the non-terrestrial network (NTN) revolution with Internet of Things (IoT) and
					Direct-to-Device (D2D)
				</p>
			</div>
			<!-- Pillar 4 -->
			<div class="py-6 lg:py-8 sm:pl-6 lg:pl-8">
				<p class="font-antarctica font-semibold text-white text-sm mb-3">
					Trusted leader in secure connectivity
				</p>
				<p class="font-antarctica font-light text-white/70 text-sm leading-relaxed">
					Provide multi-path critical connectivity solutions
				</p>
			</div>
		</div>

		<!-- Sectorial priority -->
		<div class="flex items-center gap-5 py-8 border-b border-white/20 mb-12">
			<img src="/Sectorial priority.svg" alt="Sectorial priority" class="w-14 h-14 shrink-0" />
			<div>
				<p class="font-antarctica font-semibold text-white text-sm mb-0.5">Sectorial priority</p>
				<p class="font-antarctica font-light text-white/70 text-sm">Autonomous mobility</p>
			</div>
		</div>

	</Container>
</div>
