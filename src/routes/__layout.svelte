<script lang="ts">
	import { subscribe } from 'svelte/internal';
	import DesktopNav from './DesktopNav.svelte';
	import Hamburger from './Hamburger.svelte';
	import MobileNav from './MobileNav.svelte';
	import { menu, screenwidth, open } from './Stores';

	let menuValue: number;
	let displayWidth: number;
	let displayMobileNav: boolean;

	menu.subscribe((value) => {
		menuValue = value;
	});

	screenwidth.subscribe((value) => {
		displayWidth = value;
	});

	open.subscribe((value) => {
		displayMobileNav = value;
	});
</script>

<div class="DasNav">
	{#if displayWidth > 600}
		<DesktopNav />
	{:else}
		<MobileNav />
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
