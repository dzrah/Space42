<script>
	import Container from '../../components/Container.svelte';
	import Section from '../../components/Section.svelte';

	const integrationFeatures = [
		'Satellite<br>constellations',
		'Geospatial<br>intelligence<br>platforms',
		'Digital twin<br>systems',
		'Ground<br>infrastructure<br>networks'
	];
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container class="pb-12 lg:pb-20">
		<div class="bg-white rounded-sm p-5 sm:p-8 lg:p-12">
			<!-- Title -->
			<h2 class="font-antarctica font-semibold text-[#121a6b] text-2xl lg:text-4xl uppercase tracking-wide mb-8">
				High Altitude Platform System (HAPS)
			</h2>

			<!-- Image + Text row -->
			<div class="grid grid-cols-1 md:grid-cols-2 gap-8 lg:gap-12 mb-10">
				<!-- Left: image -->
				<div class="flex items-center justify-center">
					<img
				loading="lazy" src="/_HAPS_01.webp" alt="High Altitude Platform System" class="w-full object-contain" />
				</div>

				<!-- Right: content -->
				<div class="flex flex-col gap-4">
					<h3 class="font-antarctica font-semibold text-[#121a6b] text-base lg:text-lg">
						Persistent observation and connectivity from the stratosphere
					</h3>
					<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
						High Altitude Platform Systems (HAPS) are solar-powered aircraft operating in the
						stratosphere at altitudes of approximately 18–25 kilometres.
					</p>
					<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
						Positioned between satellites and terrestrial infrastructure, HAPS platforms provide
						persistent regional coverage, enabling long-duration monitoring and communications
						services across targeted areas.
					</p>
					<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
						HAPS complement satellite systems by delivering low-latency data collection and localized
						observation capabilities, creating a multi-layer space infrastructure architecture.
					</p>
				</div>
			</div>

			<!-- Integration with Space42 infrastructure — full width -->
			<div>
				<h4 class="font-antarctica font-semibold text-[#121a6b] text-base lg:text-lg mb-3">
					Integration with Space42 infrastructure
				</h4>
				<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed mb-6">
					HAPS platforms operate as part of the Space42 multi-layer architecture, integrating with:
				</p>

				<!-- features: 2-col grid on mobile, single flex row on sm+ -->
				<div class="grid grid-cols-2 gap-4 sm:hidden">
					{#each integrationFeatures as feature}
						<div class="flex items-start gap-2">
							<div class="w-6 h-2 bg-[#f0f1f7] rounded-full shrink-0 mt-1"></div>
							<p class="font-antarctica font-semibold text-[#121a6b] text-sm leading-snug">
								{@html feature}
							</p>
						</div>
					{/each}
				</div>
				<div class="hidden sm:flex items-center">
					{#each integrationFeatures as feature, i}
						{#if i > 0}
							<div class="w-8 h-2 bg-[#f0f1f7] rounded-full shrink-0 mx-4"></div>
						{/if}
						<p class="font-antarctica font-semibold text-[#121a6b] text-sm leading-snug flex-1 text-center">
							{@html feature}
						</p>
					{/each}
				</div>

				<p class="font-antarctica font-light text-gray-600 text-sm leading-relaxed mt-6">
					This architecture enables seamless data flow between stratospheric platforms, satellites,
					and AI analytics platforms.
				</p>
			</div>
		</div>
	</Container>
</Section>
