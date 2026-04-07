<script>
	import Navbar from '../components/Navbar.svelte';
	import Footer from '../components/Footer.svelte';
	import HeroBanner from './components/HeroBanner.svelte';
	import SARIntro from './components/SARIntro.svelte';
	import ForesightCard from './components/ForesightCard.svelte';
	import HAPSCard from './components/HAPSCard.svelte';
	import PlatformsGrid from './components/PlatformsGrid.svelte';
	import ContactForm from './components/ContactForm.svelte';
</script>

<Navbar />

<div class="pt-24">
	<HeroBanner />
	<SARIntro />
	<ForesightCard />
	<HAPSCard />
	<PlatformsGrid />
	<ContactForm />
</div>

<Footer />
