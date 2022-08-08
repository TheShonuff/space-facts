<script lang="ts">
	import { menu, screenwidth } from './Stores';

	import PlanetDesktop from './PlanetDesktop.svelte';
	import PlanetMobile from './PlanetMobile.svelte';
	import { onMount } from 'svelte';

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
	<h2>inner Width: {displayWidth}</h2>
	<h2>innher height: {innerHeight}</h2>
</div>

<style global>
	.background {
		background-color: #070724;
		background-image: url(/src/assets/background-stars.svg);
		height: 100%;
		width: 100%;
	}

	html body {
		margin: 0;
	}
	nav {
		width: 100%;
	}

	.nav-container {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		padding-left: 32px;
		padding-right: 32px;
		border-bottom: 1px solid rgba(255, 255, 255, 0.5);
		border-width: thin;
		padding-top: 22px;
		padding-bottom: 22px;
	}
	#menu {
		display: flex;
		flex-direction: row;
		gap: 22px;
		font-family: 'League Spartan', sans-serif;
		font-size: 11px;
		color: white;
		line-height: 25px;
		list-style: none;
	}
	ul {
		margin: 0;
		padding-top: 10px;
		padding-inline-start: 0;
	}
	a {
		text-decoration: none;
		color: white;
		letter-spacing: 1px;
		text-transform: uppercase;
	}
	h1 {
		color: white;
		margin: 0;
		padding: 0;
	}

	h2 {
		margin: 0;
		color: white;
		font-family: 'Antonio', sans-serif;
	}

	h5 {
		margin: 0;
	}

	@media (max-width: 900px) {
		.nav-container {
			flex-direction: column;
			margin: 0 auto;
		}

		.page-title {
			margin: 0 auto;
		}

		#menu {
			display: flex;
			flex-direction: row;
			justify-content: space-between;
			padding-top: 22px;
		}
	}

	@media (max-width: 600px) {
		#menu {
			display: none;
		}
		.nav-container {
			flex-direction: row;
			justify-content: space-between;
			margin-bottom: 0;
			padding-bottom: 10px;
		}

		.nav-container .page-title {
			padding: 0;
			margin: 0;
		}
		.mobile-nav {
			background-color: #070724;
			height: 100vh;
			width: 90%;
			display: flex;
			flex-direction: column;
			margin: 0 auto;
			padding-top: 30px;
		}

		.mobile-nav img {
			height: 8px;
			width: 4px;
			padding-right: 10px;
		}

		.mobile-nav a {
			text-decoration: none;
			color: white;
			font-family: 'League Spartan', sans-serif;
			font-size: 15px;
			font-weight: 700;
			line-height: 25px;
			padding-left: 25px;
		}

		.mobile-nav li {
			display: flex;
			align-items: center;
			justify-content: space-between;
			flex-direction: row;
			padding-bottom: 10px;
			padding-top: 22px;
			border-bottom: 1px solid rgba(255, 255, 255, 0.5);
			border-width: thin;
		}
		.planet-selector {
			display: flex;
			flex-direction: row;
			width: 200px;
		}

		.planet-icon {
			height: 20px;
			width: 20px;
			border-radius: 10px;
			background-color: var(--icon-color);
		}
	}
</style>
