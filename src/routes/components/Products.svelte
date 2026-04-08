<script>
	import Carousel from './Carousel.svelte';
	import Container from './Container.svelte';
	import NextGenCard from './NextGenCard.svelte';
	import NextGenCardDown from './NextGenCardDown.svelte';
	import ProdctCard from './ProdctCard.svelte';
	import Section from './Section.svelte';

	let slides = [
		{
			id: 1,
			image: '/img-1.webp',
			title: 'DEFENSE',
			description:
				'Thuraya-4 delivers sovereign, always-on L-band connectivity for ministries of defense, interior and emergency services. Built for extreme conditions, the Thuraya-4 supports rugged, field-deployable terminals interoperable with tactical radios, enabling secure personnel/asset tracking.'
		},
		{
			id: 5,
			image: '/img-5.webp',
			title: 'ENERGY',
			description:
				'Keep remote assets online: from deserts and rigs to moving fleets. When fiber stops and cellular fades, operations still need telemetry, voice, and safety comms. Thuraya-4’s resilient L-band makes upstream and midstream sites get back on the grid, with no downtime.'
		},
		{
			id: 3,
			image: '/img-3.webp',
			title: 'MARITIME',
			description:
				'Keep fleets connected end-to-end with Thuraya-4. Seamless blue-water coverage, resilient bandwidth in harsh weather and secure data exchange. From container lines to offshore platforms, integrate crew voice, tracking, and operations.'
		},
		{
			id: 4,
			image: '/img-4.webp',
			title: 'AVIATION',
			description:
				'From airlines and air cargo to rotorcraft operators, Thuraya-4 powers reliable in-flight communications, real-time weather and route updates, and aircraft tracking. Lightweight, aviation-grade hardware meets strict standards, minimizing power draw for fixed-wing and helicopter missions.'
		}
	];
</script>

<div id="products"></div>
<!-- invisible anchor -->

<Section class="relative overflow-hidden" bgClass="bg-transparent">
	<div class="absolute inset-x-0 top-0 h-[10%] bg-[#f0f1f7] -z-1000000"></div>
	<div
		class="absolute inset-x-0 top-[10%] sm:h-[67%] h-[90%] bg-[url('/blue_dark.webp')] bg-cover bg-center -z-50"
	></div>
	<div class="absolute inset-x-0 bottom-0 sm:h-[40%] h-[5%] bg-[#f0f1f7] -z-1000000"></div>

	<Container class="flex-col w-full h-full">
		<div
			class="text-[#121a6b] font-semibold text-[1.05rem] mb-5 lg:text-left text-center scorll-mt-32"
		>
			<h1>Our Thuraya-4 Satellite Enabled Products</h1>
		</div>

		<div
			class="items-center justify-center my-6 lg:my-15 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-3 lg:gap-5 w-full"
		>
			<ProdctCard
				productUrl="https://www.thuraya.com/en/products-list/land-data/thuraya-ip-neo-m"
				title="IP NEO M"
				imgSrc="/Ip_Neo_M.webp"
				para="Portable L-band broadband for field teams that need rugged, go-anywhere connectivity in minutes."
			/>
			<ProdctCard
				productUrl="https://www.thuraya.com/en/products-list/land-data/thuraya-ip-neo-c"
				title="IP NEO C"
				imgSrc="/Ip_Neo_C.webp"
				para="Compact, carry-on satellite terminal delivering reliable voice/data for rapid deployments and remote sites."
			/>
			<ProdctCard
				productUrl="https://www.thuraya.com/en/products-list/land-data/thuraya-voyager-neo"
				title="VOYAGER NEO"
				imgSrc="/Voyageur_Neo_.webp"
				para="Mobile satcom hub that turns any vehicle or camp into a secure, shared Wi-Fi workspace off-grid."
			/>
			<ProdctCard
				productUrl="https://www.thuraya.com/en/products-list/land-data/thuraya-commander-neo"
				title="COMMANDER NEO"
				imgSrc="/Commander_Neo.webp"
				para="Vehicular L-band system for always-on comms, telemetry, and voice while on the move."
			/>
			<ProdctCard
				productUrl="https://www.thuraya.com/en/products-list/marine/orion-neo"
				title="ORION NEO"
				imgSrc="/Orion_Neo.webp"
				para="Maritime terminal providing high-uptime voice and IP data for vessels operating beyond coastal coverage."
			/>

			<ProdctCard
				productUrl="https://www.thuraya.com/en/products-list/land-voice/ttac-range"
				title="TTAC RANGE"
				imgSrc="/TTAC.webp"
				para="Extends VHF/UHF over satellite, linking ops beyond line-of-sight for instant, wide-area."
			/>
			<ProdctCard
				productUrl="https://www.thuraya.com/en/products-list/aero/uav-aero-terminal-t220"
				title="T220 System For UAV"
				imgSrc="/UAV_220.webp"
				para="Lightweight SATCOM link for unmanned aircraft, enabling BVLOS command, control, and payload data."
			/>
			<ProdctCard
				productUrl="https://www.thuraya.com/en/products-list/aero/fixed-wing-aero-terminal-t320"
				title="T320 System For Fixed-Wing"
				imgSrc="/AERO_320.webp"
				para="Airborne connectivity for fixed-wing platforms, supporting in-flight ops, tracking, and mission."
			/>
			<ProdctCard
				productUrl="https://www.thuraya.com/en/products-list/aero/rotary-wing-aero-terminal-t420"
				title="T420 System For Rotary-Wing"
				imgSrc="/Helo_420.webp"
				para="Helicopter-ready satcom engineered for vibration and rotor-wash, keeping crews connected in flight."
			/>
		</div>
		<div class="flex items-center justify-center">
			<img
				loading="lazy" class="w-full max-w-2xl" src="/T4_Map_.webp" alt="" />
		</div>
	</Container>

	<Container>
		<div id="industry">
			<div
				class="text-[#ffffff] font-semibold text-[1.2rem] lg:text-[1.7rem] lg:mb-10 mb-20 mt-20 w-full flex items-center justify-center lg:justify-start text-center lg:text-left"
			>
				<span class="md:w-[70%] w-full">
					Mission-ready satellite solutions for national security, maritime, remote business
					operations, and aviation
				</span>
			</div>

			<div>
				<Carousel {slides} autoPlay={true} interval={5000} />
				<div class="bg-[#ffffff] w-full flex-col items-center justify-center rounded-[0.2rem]">
					<div class="flex items-center justify-center">
						<div
							class="flex mt-10 font-semibold font-antarctica lg:text-[1.2rem] text-[#121a6b] text-[0.95rem]"
						>
							<h2>Thuraya-4 next-gen capabilities</h2>
						</div>
					</div>
					<div
						class="lg:grid lg:grid-cols-4 px-8 lg:gap-8 gap-1 lg:mt-15 mt-4 sm:min-h-[400px] min-h-[300px] flex flex-col pb-6 lg:pb-0"
					>
						<NextGenCardDown
							title="Advanced Technology"
							svgSrc="/Asset 5.svg"
							para="Based on the new all-electric Airbus Eurostar Neo platform."
						/>
						<NextGenCardDown
							title="Wider Satellite Footprint"
							svgSrc="/Asset 6.svg"
							para="Europe, Africa, Central Asia and the Middle East."
						/>
						<NextGenCardDown
							title="Innovative Design"
							svgSrc="/Asset 7.svg"
							para="Advanced routing flexibility of up to 3,200 channels with dynamic power allocation."
						/>
						<NextGenCardDown
							title="Versatile Platform For Future Applications"
							svgSrc="/Asset 8.svg"
							para="New product development opportunities - IoT Maritime & Government"
						/>
						<NextGenCardDown
							title="More Value"
							svgSrc="/Asset 9.svg"
							para="Affordable, reliable with flexible plans"
						/>
						<NextGenCardDown
							title="Unmatched Reliability"
							svgSrc="/Asset 10.svg"
							para="Designed with security and resilience in mind"
						/>
						<NextGenCardDown
							title="Higher Throughput"
							svgSrc="/Asset 11.svg"
							para="Wide range of data rates above 1 Mbps Efficient and smart resource management to support surge in hotspot areas"
						/>

						<!-- <div class="flex-col items-start justify-start p-5 flex-1">
						<div class="flex items-center justify-start">
							<img
				loading="lazy" class="w-50 mb-7" src="/Asset 5.svg" alt="" />
						</div>
						<div
							class="flex justify-start items-center text-[#121a6b] font-semibold sm:text-[0.9rem] text-[0.8rem] mt-2"
						>
							<span>Advanced Technology</span>
						</div>
						<div class="flex justify-start items-center">
							<p>Based on the new all-electric Airbus Eurostar Neo platform</p>
						</div>
					</div> -->
					</div>
				</div>
			</div>
		</div>
	</Container>
</Section>
