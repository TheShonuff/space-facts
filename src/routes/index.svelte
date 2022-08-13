<script lang="ts">
	import { menu, screenwidth } from './Stores';

	import PlanetDesktop from './PlanetDesktop.svelte';
	import PlanetMobile from './PlanetMobile.svelte';

	let menuValue: number;

	let innerHeight = 0;

	menu.subscribe((value) => {
		menuValue = value;
	});
	let displayWidth: number;

	screenwidth.subscribe((value) => {
		displayWidth = value;
	});
	//screen dectection
	function onChange(value: number) {
		screenwidth.set(value);
	}
</script>

<svelte:head>
	<link
		href="https://fonts.googleapis.com/css2?family=Antonio:wght@100;200;300;400;500;600;700&display=swap"
		rel="stylesheet"
	/>

	<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />

	<link
		href="https://fonts.googleapis.com/css2?family=Antonio:wght@100;200;300;400;500;600;700&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<svelte:window bind:innerWidth={$screenwidth} bind:innerHeight />

<div class="background">
	{#if $screenwidth > 600 || $screenwidth == 0}
		<PlanetDesktop />
	{:else}
		<PlanetMobile />
	{/if}
</div>

<style global src="../styles/index.css">
</style>
