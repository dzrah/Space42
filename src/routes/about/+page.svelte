<script>
	import Navbar from '../components/Navbar.svelte';
	import Footer from '../components/Footer.svelte';
	import BeyondHorizons from './components/BeyondHorizons.svelte';
	import FromOrbitToImpact from './components/FromOrbitToImpact.svelte';
	import StrategicPillars from './components/StrategicPillars.svelte';
	import FlagshipPrograms from './components/FlagshipPrograms.svelte';
	import BoardAndLeadership from './components/BoardAndLeadership.svelte';
	import FormCRM from '../FormCRM.svelte';
</script>

<Navbar />

<div class="pt-16 sm:pt-20 lg:pt-24">
	<BeyondHorizons />
	<FromOrbitToImpact />
	<StrategicPillars />
	<FlagshipPrograms />
	<BoardAndLeadership />
	<FormCRM />
</div>

<Footer />
