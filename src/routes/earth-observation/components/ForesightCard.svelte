<script>
	import Container from '../../components/Container.svelte';
	import Section from '../../components/Section.svelte';

	const analyticsFeatures = [
		'Automated<br>change<br>detection',
		'Object<br>recognition',
		'Anomaly<br>detection',
		'Predictive infrastructure monitoring'
	];
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container class="pb-12 lg:pb-20">
		<div class="bg-white rounded-sm p-5 sm:p-8 lg:p-12">
			<!-- Title -->
			<h2 class="font-antarctica font-semibold text-[#121a6b] text-2xl lg:text-4xl uppercase tracking-wide mb-8">
				Foresight SAR Constellation
			</h2>

			<!-- Image + Text row -->
			<div class="grid grid-cols-1 md:grid-cols-2 gap-8 lg:gap-12 mb-10">
				<!-- Left: image -->
				<div class="flex items-center justify-center">
					<img
				loading="lazy" src="/foresight.webp" alt="Foresight SAR Constellation" class="w-full max-w-sm object-contain" />
				</div>

				<!-- Right: content -->
				<div class="flex flex-col gap-4">
					<h3 class="font-antarctica font-semibold text-[#121a6b] text-base lg:text-lg">
						Persistent Earth observation through all-weather radar imaging
					</h3>
					<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
						The Foresight constellation is Space42's next-generation Synthetic Aperture Radar (SAR)
						satellite system, designed to provide persistent Earth observation capabilities for
						governments, infrastructure operators, and strategic industries.
					</p>
					<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
						Unlike optical satellites, SAR technology enables high-resolution imaging day and night
						and through cloud cover, ensuring continuous monitoring across large geographic areas.
					</p>
					<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
						The Foresight constellation is designed to deliver revisit frequency, reliability, and
						data continuity, supporting mission-critical monitoring applications such as national
						security, infrastructure monitoring, environmental analysis, and maritime domain
						awareness.
					</p>
				</div>
			</div>

			<!-- Integrated Analytics with GIQ — full width -->
			<div>
				<h4 class="font-antarctica font-semibold text-[#121a6b] text-base lg:text-lg mb-3">
					Integrated Analytics with GIQ
				</h4>
				<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed mb-6">
					SAR imagery from the Foresight constellation integrates directly with the GIQ geospatial
					intelligence platform, enabling advanced analytics such as:
				</p>

				<!-- features: 2-col grid on mobile, single flex row on sm+ -->
				<div class="grid grid-cols-2 gap-4 sm:hidden">
					{#each analyticsFeatures as feature}
						<div class="flex items-start gap-2">
							<div class="w-6 h-2 bg-[#f0f1f7] rounded-full shrink-0 mt-1"></div>
							<p class="font-antarctica font-semibold text-[#121a6b] text-sm leading-snug">
								{@html feature}
							</p>
						</div>
					{/each}
				</div>
				<div class="hidden sm:flex items-center">
					{#each analyticsFeatures as feature, i}
						{#if i > 0}
							<div class="w-8 h-2 bg-[#f0f1f7] rounded-full shrink-0 mx-4"></div>
						{/if}
						<p class="font-antarctica font-semibold text-[#121a6b] text-sm leading-snug flex-1 text-center">
							{@html feature}
						</p>
					{/each}
				</div>

				<p class="font-antarctica font-light text-gray-600 text-sm leading-relaxed mt-6">
					By combining satellite data with AI analytics, the platform transforms raw radar imagery
					into actionable operational intelligence.
				</p>
			</div>
		</div>
	</Container>
</Section>
