<script lang="ts">
	import { onMount } from 'svelte';
	import { fade } from 'svelte/transition';
	let isLoading = true;
	let onCover = false;

	onMount(async () => {
		setTimeout(() => {
			isLoading = false;
		}, 300);
		setTimeout(() => {
			isLoading = true;
			onCover = true;
		}, 5000);
	});
</script>

<div class="hero">
	<img
		src="/imgs/main.webp"
		alt="main iamge of wedding"
		loading="lazy"
		class="absolute inset-0 -z-10 h-full w-full object-cover"
	/>
	{#if !isLoading}
		<video
			src="/gif/main_mobile.mp4"
			class="absolute inset-0 h-full w-full object-cover md:hidden"
			autoplay
			muted
			loop
			transition:fade={{ duration: 1000 }}
		>
			<track kind="captions" />Your browser does not support the video tag
		</video>
		<video
			src="/gif/main_web.mp4"
			class="absolute inset-0 hidden h-full w-full object-cover md:block"
			autoplay
			muted
			loop
			transition:fade={{ duration: 1000 }}
		>
			<track kind="captions" />Your browser does not support the video tag
		</video>
	{/if}
	{#if onCover}
		<img
			src="/imgs/main_cover.webp"
			alt="cover of main"
			loading="lazy"
			class="absolute inset-0 -z-10 h-full w-full object-cover"
			transition:fade={{ duration: 1000 }}
		/>
	{/if}
</div>

<style lang="postcss">
	.hero {
		@apply relative h-full w-full overflow-hidden;
	}
</style>
