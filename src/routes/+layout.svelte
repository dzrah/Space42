<script>
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import Navbar from './components/Navbar.svelte';
	import { afterNavigate } from '$app/navigation';
	import { page } from '$app/state';

	let { children } = $props();

	const siteUrl = 'https://space42.ai';
	const canonicalUrl = $derived(`${siteUrl}${page.url.pathname}`);

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
	<link rel="canonical" href={canonicalUrl} />
</svelte:head>

<!-- <Navbar /> -->
{@render children()}

<style>
	/* :global(html, body) {
    font-family: 'Antarctica', sans-serif;
    font-weight: 400;
  } */
</style>
