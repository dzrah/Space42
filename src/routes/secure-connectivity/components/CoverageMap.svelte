<script>
	import Container from '../../components/Container.svelte';
	import Section from '../../components/Section.svelte';
</script>

<Section bgClass="bg-white">
	<Container class="py-12 lg:py-20">

		<!-- Top row: title + description -->
		<div class="grid grid-cols-1 md:grid-cols-2 gap-8 lg:gap-16 mb-10">
			<h2 class="font-antarctica font-semibold text-[#121a6b] text-2xl lg:text-3xl">
				Coverage map
			</h2>
			<div class="flex flex-col gap-4">
				<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
					Space42 has successfully completed the migration of all Thuraya legacy services.
				</p>
				<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
					This includes Voice, SMS, and Legacy packet data, from the Thuraya-2 satellite to
					Thuraya-4 as of February 2026.
				</p>
				<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
					These services, used across the full range of Thuraya, are now fully supported within the
					Thuraya-4 coverage footprint.
				</p>
			</div>
		</div>

		<!-- Legend -->
		<div class="flex flex-row gap-6 mb-4">
			<div class="flex items-center gap-2">
				<div
					class="w-8 h-4 rounded-sm shrink-0"
					style="background: linear-gradient(to right, #7ecef4, #1a6bb5)"
				></div>
				<div>
					<p class="font-antarctica font-semibold text-[#121a6b] text-xs uppercase tracking-wide leading-none">Coverage Available</p>
					<p class="font-antarctica font-light text-[#121a6b] text-xs">Thuraya-4</p>
				</div>
			</div>
			<div class="flex items-center gap-2">
				<div class="w-8 h-4 rounded-sm bg-[#121a6b] shrink-0"></div>
				<div>
					<p class="font-antarctica font-semibold text-[#121a6b] text-xs uppercase tracking-wide leading-none">Coverage Available</p>
					<p class="font-antarctica font-light text-[#121a6b] text-xs">Thuraya-2 & partners</p>
				</div>
			</div>
		</div>

		<!-- Map + button -->
		<div class="flex flex-col items-center gap-6">
			<img loading="lazy" src="/T4_Map_.webp" alt="Thuraya-4 coverage map" class="w-full lg:w-4/5 object-contain" />
			<a
				href="https://www.thuraya.com/en/thuraya-4-ngs/home/index.html"
				target="_blank"
				rel="noopener noreferrer"
				class="inline-block border border-[#121a6b] text-[#121a6b] px-5 py-2 text-sm font-light hover:bg-[#121a6b] hover:text-white transition-all duration-200"
			>
				Discover Thuraya-4
			</a>
		</div>

	</Container>
</Section>
