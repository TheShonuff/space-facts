<script lang="ts">
	import { prevent_default } from 'svelte/internal';
	import Earth from './Earth.svelte';
	import Jupiter from './Jupiter.svelte';
	import Mars from './Mars.svelte';
	import Mercury from './Mercury.svelte';
	import Neptune from './Neptune.svelte';
	import Saturn from './Saturn.svelte';
	import Uranus from './Uranus.svelte';
	import Venus from './Venus.svelte';
	import Hamburger from './Hamburger.svelte';
	import MediaQuery from './MediaQuery.svelte';

	import IconChevron from '../assests/icon-chevron.svg';

	export let menu = 1;

	export let open = false;
	export let toggleNav = (): void => {
		open = !open;
	};

	export function toggleMobileNav(num) {
		toggleNav();
		menu = num;
	}

	//screen dectection
	let innerWidth = 0;
	let innerHeight = 0;
</script>

<svelte:head>
	<link
		href="https://fonts.googleapis.com/css2?family=Antonio:wght@100;200;300;400;500;600;700&display=swap"
		rel="stylesheet"
	/>

	<link
		href="https://fonts.googleapis.com/css2?family=Antonio:wght@100;200;300;400;500;600;700&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<svelte:window bind:innerWidth bind:innerHeight />

<div class="background">
	<div class="nav-container">
		<div class="page-title">
			<h2>Planet Facts</h2>
		</div>
		{#if innerWidth > 600}
			<ul id="menu">
				<li>
					<a href="/" on:click|preventDefault={() => (menu = 1)}>Mercury</a>
				</li>
				<li><a href="/" on:click|preventDefault={() => (menu = 2)}>Venus</a></li>
				<li><a href="/" on:click|preventDefault={() => (menu = 3)}>Earth</a></li>
				<li><a href="/" on:click|preventDefault={() => (menu = 4)}>Mars</a></li>
				<li><a href="/" on:click|preventDefault={() => (menu = 5)}>Jupiter</a></li>
				<li><a href="/" on:click|preventDefault={() => (menu = 6)}>Saturn</a></li>
				<li><a href="/" on:click|preventDefault={() => (menu = 7)}>Uranus</a></li>
				<li><a href="/" on:click|preventDefault={() => (menu = 8)}>Neptune</a></li>
			</ul>
		{/if}

		{#if innerWidth <= 600}
			<Hamburger {open} {toggleNav} />
		{/if}
	</div>

	{#if innerWidth <= 600}
		{#if open}
			<nav class="mobile-nav">
				<li>
					<div class="planet-selector">
						<div class="planet-icon" />
						<a href="/" on:click|preventDefault={() => toggleMobileNav(1)}>Mercury</a>
					</div>
					<img src={IconChevron} alt="selector" />
				</li>
				<li>
					<div class="planet-selector">
						<div class="planet-icon" />
						<a href="/" on:click|preventDefault={() => toggleMobileNav(2)}>Venus</a>
					</div>
					<img src={IconChevron} alt="selector" />
				</li>
				<li>
					<div class="planet-selector">
						<div class="planet-icon" />
						<a href="/" on:click|preventDefault={() => toggleMobileNav(3)}>Earth</a>
					</div>
					<img src={IconChevron} alt="selector" />
				</li>
				<li>
					<div class="planet-selector">
						<div class="planet-icon" />
						<a href="/" on:click|preventDefault={() => toggleMobileNav(4)}>Mars</a>
					</div>
					<img src={IconChevron} alt="selector" />
				</li>
				<li>
					<div class="planet-selector">
						<div class="planet-icon" />
						<a href="/" on:click|preventDefault={() => toggleMobileNav(5)}>Jupiter</a>
					</div>
					<img src={IconChevron} alt="selector" />
				</li>
				<li>
					<div class="planet-selector">
						<div class="planet-icon" />
						<a href="/" on:click|preventDefault={() => toggleMobileNav(6)}>Saturn</a>
					</div>
					<img src={IconChevron} alt="selector" />
				</li>
				<li>
					<div class="planet-selector">
						<div class="planet-icon" />
						<a href="/" on:click|preventDefault={() => toggleMobileNav(7)}>uranus</a>
					</div>
					<img src={IconChevron} alt="selector" />
				</li>
				<li>
					<div class="planet-selector">
						<div class="planet-icon" />
						<a href="/" on:click|preventDefault={() => toggleMobileNav(8)}>Neptune</a>
					</div>
					<img src={IconChevron} alt="selector" />
				</li>
			</nav>
		{/if}
	{/if}
	{#if menu === 1}
		<Mercury />
	{:else if menu === 2}
		<Venus />
	{:else if menu === 3}
		<Earth />
	{:else if menu === 4}
		<Mars />
	{:else if menu === 5}
		<Jupiter />
	{:else if menu === 6}
		<Saturn />
	{:else if menu === 7}
		<Uranus />
	{:else if menu === 8}
		<Neptune />
	{:else}
		<h1>Page Not Found</h1>
	{/if}

	<h2>inner Width: {innerWidth}</h2>
	<h2>innher height: {innerHeight}</h2>
</div>

<style global>
	.background {
		background-color: #070724;
		background-image: url(/src/assests/background-stars.svg);
		height: 100vh;
		width: 100vw;
	}

	html body {
		margin: 0;
	}

	.nav-container {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		padding-left: 32px;
		padding-right: 32px;
		border-bottom: 1px solid white;
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
	}

	h2 {
		margin: 0;
		color: white;
		font-family: 'Antonio', sans-serif;
	}

	@media (max-width: 820px) {
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
		.nav-container {
			flex-direction: row;
		}

		.nav-container .page-title {
			padding: 0;
			margin: 0;
		}
		.mobile-nav {
			background-color: #070724;
			position: absolute;
			height: 100vh;
			width: 85%;
			display: flex;
			flex-direction: column;
			padding: 22px 24px 0px 24px;
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
			padding-bottom: 22px;
			padding-top: 22px;
			border-bottom: 1px solid white;
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
			background-color: white;
		}
	}
</style>
