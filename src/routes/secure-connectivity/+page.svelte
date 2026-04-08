<script>
	import Navbar from '../components/Navbar.svelte';
	import Footer from '../components/Footer.svelte';
	import HeroBanner from './components/HeroBanner.svelte';
	import GeostatCapabilities from './components/GeostatCapabilities.svelte';
	import ProductPortfolio from './components/ProductPortfolio.svelte';
	import ConnectForm from './components/ConnectForm.svelte';
	import CoverageMap from './components/CoverageMap.svelte';
</script>

<Navbar />

<div class="pt-16 sm:pt-20 lg:pt-24">
	<HeroBanner />
	<GeostatCapabilities />
	<ProductPortfolio />
	<ConnectForm />
	<CoverageMap />
</div>

<Footer />
