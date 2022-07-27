<script lang="ts">
	import IconChevron from '../assests/icon-chevron.svg';
	import Hamburger from './Hamburger.svelte';
	import { menu, open } from './Stores';
	let menuValue: number;

	function toggleMobileNav(num) {
		menu.set(num);
	}
</script>

<nav class="mobile-nav">
	<h1>Planet Facts Mobile</h1>
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
