<script>
	import Container from './Container.svelte';
	import Section from './Section.svelte';
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container class="py-12 lg:py-20">
		<div class="flex flex-col md:flex-row items-center gap-10 lg:gap-16">
			<!-- Left: Magazine cover -->
			<a
				href="https://www.space42.ai/en/the-orbit-magazine"
				target="_blank"
				class="flex-shrink-0 w-48 sm:w-56 md:w-64 lg:w-72"
			>
				<img
					loading="lazy"
					src="/the orbit front page.webp"
					alt="The Orbit Magazine"
					class="w-full shadow-lg"
				/>
			</a>

			<!-- Right: Text content -->
			<div class="flex flex-col gap-4 max-w-xl">
				<h2 class="font-antarctica font-semibold text-[#121a6b] text-2xl lg:text-3xl leading-snug">
					Discover The Orbit<br />Space42's Flagship Magazine
				</h2>
				<p class="font-antarctica font-light text-sm lg:text-base leading-relaxed text-gray-700">
					Explore perspectives from Space42's leaders, engineers, and product teams on what becomes
					possible when space capabilities move from isolated systems to integrated platforms. The
					Orbit explores how universal connectivity, sovereign communications, AI-driven geospatial
					intelligence, and autonomous mobility are transforming industries and nations. Bringing
					forward human stories of innovation, from telemedicine reaching remote communities to the
					UAE's next generation of space leaders.
				</p>
				<div class="mt-2">
					<a
						href="https://www.space42.ai/en/the-orbit-magazine"
						target="_blank"
						rel="noopener noreferrer"
						class="inline-block border border-[#121a6b] text-[#121a6b] px-5 py-2 text-sm font-light hover:bg-[#121a6b] hover:text-white transition-all duration-200"
					>
						Read articles
					</a>
				</div>
			</div>
		</div>
	</Container>
</Section>
