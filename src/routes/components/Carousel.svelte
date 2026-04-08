<script lang="ts">
	import { onDestroy, onMount } from 'svelte';

	import { fade } from 'svelte/transition';

	let { slides = [], autoPlay = true, interval = 5000 } = $props();

	let currentIndex = $state(0);
	let isPaused = $state(false);
	let autoPlayInterval: number | undefined;

	let totalSlides = $derived(slides.length);

	function next() {
		currentIndex = (currentIndex + 1) % totalSlides;
	}

	function prev() {
		currentIndex = (currentIndex - 1 + totalSlides) % totalSlides;
	}

	function goTO(index: number) {
		currentIndex = index;
	}

	function handleKeydown(event: KeyboardEvent) {
		if (event.key === 'ArrowLeft') prev();
		if (event.key === 'ArrowRight') next();
	}

	onMount(() => {
		if (autoPlay) {
			autoPlayInterval = setInterval(() => {
				if (!isPaused) next();
			}, interval);
		}
	});

	onDestroy(() => {
		if (autoPlayInterval) clearInterval(autoPlayInterval);
	});
</script>

<svelte:window onkeydown={handleKeydown} />

<section
	role="presentation"
	class="relative"
	onmouseenter={() => {
		isPaused = true;
	}}
	onmouseleave={() => {
		isPaused = false;
	}}
>
	<div class="grid grid-cols-1 md:grid-cols-2 gap-4 md:gap-8 items-end w-full min-h-[300px] md:min-h-[400px]">
		<div class="relative flex items-end justify-center w-full h-full">
			<button
				onclick={prev}
				class="absolute top-[50%] left-0 z-10 text-blue-500 hover:text-blue-400 transition-colors p-0 cursor-pointer"
				aria-label="Previous slide"
			>
				<svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M15 19l-7-7 7-7"
					/>
				</svg>
			</button>

			{#key currentIndex}
				<img
					src={slides[currentIndex].image}
					alt={slides[currentIndex].title}
					class="max-h-[300px] object-contain flex items-start justify-center"
					in:fade={{ duration: 200 }}
				/>
			{/key}

			<button
				onclick={next}
				class="absolute top-[50%] right-0 z-10 text-blue-500 hover:text-blue-400 transition-colors p-0 cursor-pointer"
				aria-label="Next slide"
			>
				<svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
				</svg>
			</button>
		</div>

		<div class="flex-col justify-center items-center">
			{#key currentIndex}
				<div
					class="text-white flex-col items-center justify-center"
					in:fade={{ duration: 200 }}
				>
					<h2 class="text-base sm:text-xl lg:text-2xl font-semibold mb-4">
						{slides[currentIndex].title}
					</h2>
					<p class="text-white/80 leading-relaxed text-xs sm:text-sm lg:text-base">
						{slides[currentIndex].description}
					</p>
				</div>
			{/key}

			<div class="flex justify-end gap-2 mb-7">
				{#each slides as _, index}
					<button
						onclick={() => goTO(index)}
						class="w-3 h-3 rounded-full transition-color cursor-pointer {currentIndex === index
							? 'bg-blue-300'
							: 'bg-blue-700'}"
						aria-label="Go to slide {index + 1}"
						aria-current={currentIndex === index}
					>
					</button>
				{/each}
			</div>
		</div>
	</div>
</section>
