<script lang="ts">
	import Container from '../../components/Container.svelte';
	import Section from '../../components/Section.svelte';

	function handleImgError(e: Event) {
		const img = e.currentTarget as HTMLImageElement;
		img.style.display = 'none';
		img.parentElement?.classList.add('placeholder-avatar');
	}

	const leadershipTeam = [
		{
			name: 'Karim Michel Sabbagh',
			title: 'Managing Director',
			photo: '/Karim.webp'
		},
		{
			name: 'Hasan Al Hosani',
			title: 'Chief Executive Officer of Smart Solutions',
			photo: '/Hasan.webp'
		},
		{
			name: 'Ali Al Hashami',
			title: 'Chief Executive Officer of Space Services',
			photo: '/Ali.webp'
		},
		{
			name: 'Abdulla Al Shamsi',
			title: 'Chief Business Support Officer',
			photo: '/Abdulla.webp'
		},
		{
			name: 'Maymee Kurian',
			title: 'Interim Chief Human Capital Officer',
			photo: '/Maymee.webp'
		},
		{
			name: 'Sulaiman Al Ali',
			title: 'Chief Commercial Officer',
			photo: '/Sulaiman.webp'
		},
		{
			name: 'Andrew Cole',
			title: 'Chief Financial Officer',
			photo: '/Andrew Cole.webp'
		},
		{
			name: 'Andrew Hodgman',
			title: 'General Counsel',
			photo: '/Andrew Hodgman.webp'
		},
		{
			name: 'Christian Andersen',
			title: 'Senior Vice President of Marketing and Communications',
			photo: '/Christian.webp'
		}
	];
</script>

<Section
	bgClass="bg-[url('/blue_dark.webp')] bg-cover bg-center"
>
	<Container class="py-16 lg:py-24">
		<!-- Leadership Team -->
		<h2 class="font-antarctica font-semibold text-white text-2xl lg:text-3xl mb-12">
			Leadership Team
		</h2>

		<div class="grid grid-cols-3 gap-x-8 gap-y-12">
			{#each leadershipTeam as member}
				<div class="flex flex-col items-start gap-3">
					<!-- Circular photo -->
					<div
						class="w-24 h-24 lg:w-28 lg:h-28 rounded-full overflow-hidden ring-2 ring-[#1a3a6b] bg-[#0a1840] flex-shrink-0"
					>
						<img
				loading="lazy"
							src={member.photo}
							alt={member.name}
							class="w-full h-full object-cover"
							onerror={handleImgError}
						/>
					</div>
					<!-- Name & title -->
					<div>
						<p class="font-antarctica font-semibold text-white text-xs lg:text-sm leading-snug">
							{member.name}
						</p>
						<p class="font-antarctica font-light text-[#8eaed4] text-xs mt-0.5">
							{member.title}
						</p>
					</div>
				</div>
			{/each}
		</div>
	</Container>
</Section>

<style>
	:global(.placeholder-avatar) {
		background: linear-gradient(135deg, #0d2150 0%, #1a3a6b 100%);
	}
</style>
