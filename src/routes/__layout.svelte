<script lang="ts">
	import { subscribe } from 'svelte/internal';
	import DesktopNav from './DesktopNav.svelte';
	import Hamburger from './Hamburger.svelte';
	import MobileNav from './MobileNav.svelte';
	import { menu, width } from './Stores';

	let menuValue: number;
	let screenWidth: number;

	menu.subscribe((value) => {
		menuValue = value;
	});

	width.subscribe((value) => {
		screenWidth = value;
	});
</script>

<div class="DasNav">
	<DesktopNav />
	{#if screenWidth <= 600}
		<Hamburger />
	{/if}
</div>

<slot />

<style>
	.DasNav {
		display: flex;
		width: 100%;
		flex-direction: row;
		background-color: #070724;
		justify-content: space-between;
		background-image: url(/src/assests/background-stars.svg);
		margin: 0;
	}
</style>
