<script>
	import Container from './Container.svelte';
	import NextGenCard from './NextGenCard.svelte';
	import Section from './Section.svelte';
</script>

<div id="next-gen">
	<Section bgClass="bg-[#f0f1f7]">
		<Container class="py-12 lg:py-20">
			<div class="flex w-full items-center justify-center lg:justify-start">
				<h1 class="font-semibold font-antarctica lg:text-[1.4rem] text-[#121a6b] text-[1.1rem]">
					Next Generation Satellite
				</h1>
			</div>
			<div
				class="items-center justify-center lg:my-15 my-8 grid lg:grid-cols-4 lg:gap-12 gap-3 w-full"
			>
				<NextGenCard
					title="Sovereign L-Band Coverage"
					svgSrc="/Asset 1.svg"
					para="Thuraya-4 delivers jam-proof, secure, high-uptime connectivity across Europe, MENA, Central Asia and Africa."
				/>
				<NextGenCard
					title="Built for Critical Operators"
					svgSrc="/Asset 2.svg"
					para=" Designed for governments, fleets and aviation, eliminating shadow zones where uninterrupted communication is essential."
				/>
				<NextGenCard
					title="Advanced Secure Ecosystem"
					svgSrc="/Asset 3.svg"
					para="Integrates military-grade encryption, dynamic beam steering and always-on service in a unified, partner-delivered platform."
				/>
				<NextGenCard
					title="Mission Assurance & Future Readiness"
					svgSrc="/Asset 4.svg"
					para="Keeps operations online—on land, sea and air—reducing downtime, enabling real-time data, and preparing networks for next-generation applications."
				/>
			</div>
		</Container>
	</Section>
</div>
