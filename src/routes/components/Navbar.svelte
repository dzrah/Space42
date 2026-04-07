<script>
	import Container from './Container.svelte';
	import Section from './Section.svelte';

	let isOpen = $state(false);
	let solutionsOpen = $state(false);
	let solutionsMobileOpen = $state(false);

	const solutions = [
		{ label: 'Secure Connectivity', description: 'Reliable communications on Earth.', href: '/secure-connectivity' },
		{ label: 'Earth Observation', description: 'Understanding the planet through sovereign space infrastructure.', href: '/earth-observation' },
		{ label: 'Geospatial Intelligence', description: 'Turning space data into actionable insight.', href: '/earth-observation#giq' },
		{ label: 'Integrated Systems', description: 'Autonomous mobility powered by space.', href: '/autonomous-mobility' }
	];

	function toggleMenu() {
		isOpen = !isOpen;
	}

	function closeMenu() {
		isOpen = false;
		solutionsMobileOpen = false;
	}
</script>

<Section bgClass="bg-[#121a6b]" class="z-50 fixed top-0 left-0 right-0">
	<Container>
		<nav
			class="flex items-center justify-between flex-1 text-white py-10 w-full h-full text-[0.9rem]"
		>
			<div class="flex justify-start items-start w-auto h-full">
				<a href="/" class="flex items-center justify-start"
					><img class="w-35" src="/Logo.svg" alt="" /></a
				>
			</div>

			<button
				onclick={toggleMenu}
				class="lg:hidden flex flex-col items-center justify-center w-10 h-10 gap-1.5"
				aria-label="Menu"
				><span
					class="w-6 h-0.5 bg-white transition-all duration-300 {isOpen
						? 'rotate-45 translate-y-2'
						: ''}"
				></span>
				<span class="w-6 h-0.5 bg-white transition-all duration-300 {isOpen ? 'opacity-0' : ''}"
				></span>
				<span
					class="w-6 h-0.5 bg-white transition-all duration-300 {isOpen
						? '-rotate-45 -translate-y-2'
						: ''}"
				></span></button
			>

			<div
				class="hidden lg:flex items-center justify-between h-full w-auto gap-10 font-extralight text-white"
			>
				<a class="hover:opacity-80 transition-opacity opacity-100" href="/about">About Us</a>

				<!-- Solutions dropdown -->
				<div
					role="navigation"
					class="relative"
					onmouseenter={() => (solutionsOpen = true)}
					onmouseleave={() => (solutionsOpen = false)}
				>
					<button
						class="flex items-center gap-1 hover:opacity-80 transition-opacity font-extralight"
						onclick={() => (solutionsOpen = !solutionsOpen)}
					>
						Solutions
						<svg
							class="w-3 h-3 transition-transform duration-200 {solutionsOpen ? 'rotate-180' : ''}"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							viewBox="0 0 24 24"
						>
							<path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
						</svg>
					</button>

					{#if solutionsOpen}
						<!-- invisible bridge fills the gap so mouseleave doesn't fire -->
						<div class="absolute top-full left-0 right-0 h-3"></div>
						<div
							class="absolute top-full left-1/2 -translate-x-1/2 mt-3 w-64 bg-[#0d1659] border border-white/10 rounded-sm shadow-2xl z-50 overflow-hidden"
							style="animation: dropdownIn 0.15s ease-out both;"
						>
							<!-- top accent line -->
							<div class="h-0.5 w-full bg-linear-to-r from-[#0a82dc] to-[#9bd8ff]"></div>

							<div class="py-2">
								{#each solutions as s, i}
									<a
										href={s.href}
										class="group flex items-start justify-between px-5 py-3.5 hover:bg-white/5 transition-colors duration-150"
										onclick={() => (solutionsOpen = false)}
									>
										<span class="flex flex-col">
											<span class="text-[0.82rem] font-light text-white group-hover:text-[#9bd8ff] transition-colors leading-snug">
												{s.label}
											</span>
											<span class="text-[0.72rem] font-extralight text-white/45 group-hover:text-white/60 transition-colors mt-0.5 leading-snug">
												{s.description}
											</span>
										</span>
										<svg class="mt-1 w-3 h-3 shrink-0 text-white/20 group-hover:text-[#9bd8ff] group-hover:translate-x-0.5 transition-all duration-150" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
											<path stroke-linecap="round" stroke-linejoin="round" d="M9 5l7 7-7 7"/>
										</svg>
									</a>
									{#if i < solutions.length - 1}
										<div class="mx-5 h-px bg-white/5"></div>
									{/if}
								{/each}
							</div>
						</div>
					{/if}
				</div>

				<a class="hover:opacity-80 transition-opacity" href="https://space42.ai/en/investor-relations" target="_blank" rel="noopener noreferrer">Investor Relations</a>
				<a class="hover:opacity-80 transition-opacity" href="https://space42.ai/en/press-release" target="_blank" rel="noopener noreferrer">Media</a>
			</div>
			<div class="hidden lg:flex">
				<a
					class="inline-block border border-white text-white px-5 py-2 text-sm font-light hover:bg-white hover:text-[#121a6b] transition-all duration-200"
					href="#contact">Contact Us</a
				>
			</div>
		</nav>
	</Container>

	{#if isOpen}
		<div class="lg:hidden bg-[#121a6b] border-t border-white/10 flex">
			<Container>
				<div class="flex flex-col py-4 gap-4 font-extralight text-white">
					<a href="/about" class="py-2 hover:opacity-80 transition-opacity" onclick={closeMenu}>
						About Us
					</a>

					<!-- Mobile solutions accordion -->
					<div>
						<button
							class="w-full flex items-center justify-between py-2 hover:opacity-80 transition-opacity"
							onclick={() => (solutionsMobileOpen = !solutionsMobileOpen)}
						>
							<span>Solutions</span>
							<svg
								class="w-3 h-3 transition-transform duration-200 {solutionsMobileOpen ? 'rotate-180' : ''}"
								fill="none"
								stroke="currentColor"
								stroke-width="2"
								viewBox="0 0 24 24"
							>
								<path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
							</svg>
						</button>

						{#if solutionsMobileOpen}
							<div class="flex flex-col pl-4 gap-1 mt-1 border-l border-white/20">
								{#each solutions as s}
									<a
										href={s.href}
										class="py-2 text-sm hover:opacity-80 transition-opacity"
										onclick={closeMenu}
									>
										{s.label}
									</a>
								{/each}
							</div>
						{/if}
					</div>

					<a href="https://space42.ai/en/investor-relations" target="_blank" rel="noopener noreferrer" class="py-2 hover:opacity-80 transition-opacity" onclick={closeMenu}>
						Investor Relations
					</a>
					<a href="https://space42.ai/en/press-release" target="_blank" rel="noopener noreferrer" class="py-2 hover:opacity-80 transition-opacity" onclick={closeMenu}>
						Media
					</a>
					<a
						href="#contact"
						class="inline-block border border-white text-white px-5 py-2 text-sm font-light text-center hover:bg-white hover:text-[#121a6b] transition-all duration-200"
						onclick={closeMenu}
					>
						Contact Us
					</a>
				</div>
			</Container>
		</div>
	{/if}
</Section>
