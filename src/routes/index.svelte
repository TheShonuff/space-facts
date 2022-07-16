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

	export let menu = 1;
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

<div class="background">
	<div class="nav-container">
		<div class="page-title">
			<h2>Planet Facts</h2>
		</div>
		<ul id="menu">
			<li><a href="/" on:click|preventDefault={() => (menu = 1)}>Mercury</a></li>
			<li><a href="/" on:click|preventDefault={() => (menu = 2)}>Venus</a></li>
			<li><a href="/" on:click|preventDefault={() => (menu = 3)}>Earth</a></li>
			<li><a href="/" on:click|preventDefault={() => (menu = 4)}>Mars</a></li>
			<li><a href="/" on:click|preventDefault={() => (menu = 5)}>Jupiter</a></li>
			<li><a href="/" on:click|preventDefault={() => (menu = 6)}>Saturn</a></li>
			<li><a href="/" on:click|preventDefault={() => (menu = 7)}>Uranus</a></li>
			<li><a href="/" on:click|preventDefault={() => (menu = 8)}>Neptune</a></li>
		</ul>
	</div>
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

	@media (max-width: 400px) {
	}
</style>
