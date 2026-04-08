<script>
	import Navbar from '../components/Navbar.svelte';
	import Footer from '../components/Footer.svelte';
	import HeroBanner from './components/HeroBanner.svelte';
	import AutoMobilityIntro from './components/AutoMobilityIntro.svelte';
	import FleetOperationsCards from './components/FleetOperationsCards.svelte';
	import MobilityForm from './components/MobilityForm.svelte';
</script>

<Navbar />

<div class="pt-16 sm:pt-20 lg:pt-24">
	<HeroBanner />
	<AutoMobilityIntro />
	<FleetOperationsCards />
	<MobilityForm />
</div>

<Footer />
