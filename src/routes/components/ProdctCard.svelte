<script>
	let { imgSrc, title, para, productUrl } = $props();

	let isHover = $state(false);
</script>

<a href={productUrl} target="_blank" rel="noopener noreferrer">
	<div
		class="group bg-white flex flex-col items-start w-full rounded-[0.2rem] h-full cursor-pointer"
	>
		<div class="flex-col w-full items-start p-5 flex-1">
			<div class="w-full h-32 sm:h-36 lg:h-40 flex items-center justify-center lg:justify-start">
				{#if imgSrc}
					<img class="w-70 h-full object-contain" src={imgSrc} alt="" />
				{/if}
			</div>
			<div
				class="text-[#121a6b] font-semibold sm:text-[0.8rem] text-[0.8rem] mt-2 lg:text-left text-center"
			>
				<span>{title}</span>
			</div>
			<div
				class="text-xs lg:text-[0.8rem] w-full flex mt-2 lg:justify-start justify-center text-center lg:text-left line-clamp-3"
			>
				<p>{para}</p>
			</div>
		</div>

		<!-- Animated bar at bottom -->
		<div class="relative w-full h-[0.3rem] bg-[#9bd8ff] overflow-hidden mt-auto">
			<div
				class="absolute inset-0 bg-[#121a6b] origin-left scale-x-0 group-hover:scale-x-100 transition-transform duration-500 ease-out"
			></div>
		</div>
	</div>
</a>
