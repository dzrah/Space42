<script lang="ts">
	import Container from '../../components/Container.svelte';
	import Section from '../../components/Section.svelte';

	let muted = $state(true);
	let videoEl: HTMLVideoElement;

	function toggleMute() {
		muted = !muted;
		videoEl.muted = muted;
	}
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container class="py-12 lg:py-20">
		<h2 class="font-antarctica font-semibold text-[#121a6b] text-xl lg:text-3xl mb-10">
			From orbit to impact
		</h2>

		<div class="grid grid-cols-1 md:grid-cols-2 gap-8 lg:gap-16 items-start">
			<!-- Left: Video -->
			<div class="relative w-full aspect-video bg-black">
				<video
					bind:this={videoEl}
					src="/Space42 Brand Film-optimized.mp4"
					autoplay
					muted
					loop
					playsinline
					preload="metadata"
					class="w-full h-full object-cover"
					oncontextmenu={(e) => e.preventDefault()}
				></video>

				<!-- Mute/Unmute button -->
				<button
					onclick={toggleMute}
					class="absolute bottom-3 right-3 bg-black/60 hover:bg-black/80 text-white rounded-full p-2 transition-all duration-200 cursor-pointer"
					aria-label={muted ? 'Unmute' : 'Mute'}
				>
					{#if muted}
						<!-- Muted icon -->
						<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z"
							/>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M17 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2"
							/>
						</svg>
					{:else}
						<!-- Unmuted icon -->
						<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M15.536 8.464a5 5 0 010 7.072M12 6v12m-3.536-9.536a5 5 0 000 7.072M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z"
							/>
						</svg>
					{/if}
				</button>
			</div>

			<!-- Right: Text -->
			<div class="flex flex-col gap-4 text-gray-700">
				<p class="font-antarctica font-light text-sm lg:text-base leading-relaxed">
					Behind every Space42 capability is a team turning data into decisions and technology into
					outcomes.
				</p>
				<p class="font-antarctica font-light text-sm lg:text-base leading-relaxed">
					By integrating satellite communications, Earth observation, and AI-driven intelligence,
					Space42 enables a continuous flow, from insight to action.
				</p>
			</div>
		</div>
	</Container>
</Section>
