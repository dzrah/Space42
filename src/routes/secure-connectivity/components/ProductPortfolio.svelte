<script>
	import Container from '../../components/Container.svelte';
	import Section from '../../components/Section.svelte';
	import ProdctCard from '../../components/ProdctCard.svelte';

	const products = [
		{
			title: 'THURAYA ONE SATELLITE SMARTPHONE',
			description: 'Universal smartphone with cellular and satellite connectivity.',
			image: '/thuraya-one1.webp',
			url: 'https://www.thuraya.com/en/products-list/land-voice/thuraya-one'
		},
		{
			title: 'XT-PRO',
			description: 'Rugged and robust satellite handset equipped with a long battery life.',
			image: '/XT-PRO.webp',
			url: 'https://www.thuraya.com/en/products-list/land-voice/thuraya-xt-pro'
		},
		{
			title: 'XT-PRO DUAL',
			description:
				'Highly ruggedized dual-mode, dual SIM phone, with advanced navigation capabilities.',
			image: '/XT_Pro_Dual.webp',
			url: 'https://www.thuraya.com/en/products-list/land-voice/thuraya-xt-pro-dual'
		},
		{
			title: 'FDU-XT NEO',
			description:
				'Home and office docking adapter, allowing use of Thuraya XT and XT PRO satellite phones indoors.',
			image: '/FDU-XT with new logo mar 2026.webp',
			url: 'https://www.thuraya.com/en/products-list/legacy/fdu-xt'
		},
		{
			title: 'XT-LITE',
			description: 'Great value satellite phone, delivering reliable satellite connectivity.',
			image: '/XT-LITE new logo.webp',
			url: 'https://www.thuraya.com/en/products-list/land-voice/thuraya-xt-lite'
		},
		{
			title: 'IP NEO C',
			description:
				'Compact, carry-on satellite terminal delivering reliable voice/data for rapid deployments and remote sites.',
			image: '/Ip_Neo_C.webp',
			url: 'https://www.thuraya.com/en/products-list/land-data/thuraya-ip-neo-c'
		},
		{
			title: 'IP NEO M',
			description:
				'Portable L-band broadband for field teams that need rugged, go-anywhere connectivity in minutes.',
			image: '/Ip_Neo_M.webp',
			url: 'https://www.thuraya.com/en/products-list/land-data/thuraya-ip-neo-m'
		},
		{
			title: 'VOYAGER NEO',
			description:
				'Mobile satcom hub that turns any vehicle or camp into a secure, shared Wi-Fi workspace off-grid.',
			image: '/Voyageur_Neo_.webp',
			url: 'https://www.thuraya.com/en/products-list/land-data/thuraya-voyager-neo'
		},
		{
			title: 'COMMANDER NEO',
			description:
				'Vehicular L-band system for always-on comms, telemetry, and voice while on the move.',
			image: '/Commander_Neo.webp',
			url: 'https://www.thuraya.com/en/products-list/land-data/thuraya-commander-neo'
		},
		{
			title: 'ORION NEO',
			description:
				'Maritime terminal providing high-uptime voice and IP data for vessels operating beyond coastal coverage.',
			image: '/Orion_Neo.webp',
			url: 'https://www.thuraya.com/en/products-list/marine/orion-neo'
		},
		{
			title: 'MOBILE GATEWAY C WITH IP HANDSET',
			description:
				'Turns any NEO terminal into a multi-user hub. Robust voice, data, and PTT with auto-tracking, rugged IPx6 design, and hot field-deployment.',
			image: '/SPACE42_MGC_HS_2026.webp',
			url: 'https://www.thuraya.com/en/products-list/land-data/mobile-gateway-neo-c'
		},
		{
			title: 'MOBILE GATEWAY M WITH IP HANDSET',
			description:
				'Turns any NEO terminal into a multi-user hub for rugged maritime environments with robust voice and data.',
			image: '/SPACE42_MGM_HS_OCT2024.webp',
			url: 'https://www.thuraya.com/en/products-list/land-data/mobile-gateway-neo-m'
		},
		{
			title: 'AERO 320',
			description:
				'Compact, aviation-grade L-band terminal for fixed-wing aircraft, supporting in-flight ops, tracking, and mission comms.',
			image: '/AERO_320.webp',
			url: 'https://www.thuraya.com/en/products-list/aero/fixed-wing-aero-terminal-t320'
		},
		{
			title: 'HELO 420',
			description:
				'Helicopter-ready satcom engineered for vibration and rotor-wash, keeping crews connected in flight.',
			image: '/Helo_420.webp',
			url: 'https://www.thuraya.com/en/products-list/aero/rotary-wing-aero-terminal-t420'
		},
		{
			title: 'UAV 220',
			description:
				'Lightweight SATCOM link for unmanned aircraft, enabling BVLOS command, control, and payload data.',
			image: '/UAV_220.webp',
			url: 'https://www.thuraya.com/en/products-list/aero/uav-aero-terminal-t220'
		},
		{
			title: 'TTAC RANGE',
			description:
				'Extends VHF/UHF radio beyond line-of-sight over satellite, linking dispersed assets across land and at sea.',
			image: '/TTAC.webp',
			url: 'https://www.thuraya.com/en/products-list/land-voice/ttac-range'
		},
		{
			title: 'MBH',
			description:
				'Dependable satellite communications wherever your growth includes trading ships.',
			image: '/MBH.webp',
			url: 'https://www.thuraya.com/en/products-list/land-data/thuraya-mbh'
		},
		{
			title: 'MARINESTAR',
			description:
				'Most affordable maritime satellite voice solution with tracking and monitoring capabilities.',
			image: '/MarineStar.webp',
			url: 'https://www.thuraya.com/en/products-list/marine/thuraya-marinestar'
		}
	];
</script>

<Section class="relative overflow-hidden" bgClass="bg-transparent">
	<!-- Gray top -->
	<div class="absolute inset-x-0 top-0 h-[15%] bg-[#f0f1f7] -z-10"></div>
	<!-- Dark blue bottom -->
	<div
		class="absolute inset-x-0 top-[15%] bottom-0 bg-[url('/blue_dark.webp')] bg-cover bg-center -z-10"
	></div>

	<Container class="py-12 lg:py-20">
		<h2 class="font-antarctica font-semibold text-[#121a6b] text-xl lg:text-2xl mb-10">
			Secure, reliable satellite enabled communications portfolio
		</h2>

		<div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-3 lg:gap-5">
			{#each products as product}
				<ProdctCard
					productUrl={product.url}
					title={product.title}
					imgSrc={product.image}
					para={product.description}
				/>
			{/each}
		</div>
	</Container>
</Section>
