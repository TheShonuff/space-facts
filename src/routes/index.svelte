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

<div class="background">
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
	ul#menu li {
		display: inline;
		margin: 0;
	}
	a {
		text-decoration: none;
	}
	h1 {
		color: white;
	}
</style>
