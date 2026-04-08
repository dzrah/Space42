<script>
	import Container from '../../components/Container.svelte';
	import Section from '../../components/Section.svelte';
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container class="py-12 lg:py-20">
		<h2 class="font-antarctica font-semibold text-[#121a6b] text-xl lg:text-2xl mb-8">
			Space42's sovereign SAR constellation
		</h2>

		<div class="grid grid-cols-1 md:grid-cols-2 gap-8 lg:gap-16">
			<div class="flex flex-col gap-4">
				<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
					Foresight is Space42's sovereign Synthetic Aperture Radar (SAR) constellation, designed to
					deliver continuous, high-resolution Earth observation in all weather conditions.
				</p>
				<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
					For customers, this means no loss of visibility. Operations can be monitored consistently
					across borders, infrastructure, and environments regardless of weather, light, or terrain.
					What was previously intermittent or delayed becomes continuous and reliable insight.
				</p>
			</div>
			<div class="flex flex-col gap-4">
				<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
					Foresight strengthens Space42's position as a sovereign provider of end-to-end geospatial
					intelligence, enabling both the data layer and the analytics layer.
				</p>
				<p class="font-antarctica font-light text-gray-700 text-sm leading-relaxed">
					Integrated with Space42's AI-driven platform, GIQ, Foresight data is transformed into
					actionable insight at speed and scale, turning persistent observation into immediate
					operational advantage.
				</p>
			</div>
		</div>
	</Container>
</Section>
