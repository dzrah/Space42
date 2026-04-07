<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import Navbar from './components/Navbar.svelte';
	import { afterNavigate } from '$app/navigation';

	let { children } = $props();

	afterNavigate(() => {
		const hash = window.location.hash;
		if (!hash) return;
		setTimeout(() => {
			const el = document.querySelector(hash);
			if (!el) return;
			el.scrollIntoView({ behavior: 'smooth', block: 'start' });
		}, 100);
	});
</script>

<!-- <nav class="w-full bg-blue-700 z-100000 h-30"></nav> -->

<svelte:head>
	<title>Space42</title>
	<link rel="icon" href={favicon} />
</svelte:head>

<!-- <Navbar /> -->

{@render children()}

<style>
	/* :global(html, body) {
		font-family: 'Antarctica', sans-serif;
		font-weight: 400;
	} */
</style>
