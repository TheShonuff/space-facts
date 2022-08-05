<script lang="ts">
	import IconChevron from '../assets/icon-chevron.svg';
	import Hamburger from './Hamburger.svelte';
	import { menu, open } from './Stores';

	let displayMobileNav: boolean;

	open.subscribe((value) => {
		displayMobileNav = value;
	});

	function toggleMobileNav(num: number) {
		menu.set(num);
		displayMobileNav = !displayMobileNav;
		open.set(displayMobileNav);
	}

	const colors = [
		'#DEF4FC',
		'#F7CC7F',
		'#545BFE',
		'#FF6A45',
		'#ECAD7A',
		'#FCCB6B',
		'#65F0D5',
		'#497EFA'
	];
</script>

<nav>
	<div class="nav-container">
		<h2>THE PLANETS</h2>
		<Hamburger />
	</div>
	{#if $open}
		<div class="mobile-nav">
			<li>
				<div class="planet-selector">
					<div class="planet-icon" style="--icon-color:{colors[0]}" />
					<a href="/" on:click|preventDefault={() => toggleMobileNav(1)}>Mercury</a>
				</div>
				<img src={IconChevron} alt="selector" />
			</li>
			<li>
				<div class="planet-selector">
					<div class="planet-icon" style="--icon-color:{colors[1]}" />
					<a href="/" on:click|preventDefault={() => toggleMobileNav(2)}>Venus</a>
				</div>
				<img src={IconChevron} alt="selector" />
			</li>
			<li>
				<div class="planet-selector">
					<div class="planet-icon" style="--icon-color:{colors[2]}" />
					<a href="/" on:click|preventDefault={() => toggleMobileNav(3)}>Earth</a>
				</div>
				<img src={IconChevron} alt="selector" />
			</li>
			<li>
				<div class="planet-selector">
					<div class="planet-icon" style="--icon-color:{colors[3]}" />
					<a href="/" on:click|preventDefault={() => toggleMobileNav(4)}>Mars</a>
				</div>
				<img src={IconChevron} alt="selector" />
			</li>
			<li>
				<div class="planet-selector">
					<div class="planet-icon" style="--icon-color:{colors[4]}" />
					<a href="/" on:click|preventDefault={() => toggleMobileNav(5)}>Jupiter</a>
				</div>
				<img src={IconChevron} alt="selector" />
			</li>
			<li>
				<div class="planet-selector">
					<div class="planet-icon" style="--icon-color:{colors[5]}" />
					<a href="/" on:click|preventDefault={() => toggleMobileNav(6)}>Saturn</a>
				</div>
				<img src={IconChevron} alt="selector" />
			</li>
			<li>
				<div class="planet-selector">
					<div class="planet-icon" style="--icon-color:{colors[6]}" />
					<a href="/" on:click|preventDefault={() => toggleMobileNav(7)}>uranus</a>
				</div>
				<img src={IconChevron} alt="selector" />
			</li>
			<li>
				<div class="planet-selector">
					<div class="planet-icon" style="--icon-color:{colors[7]}" />
					<a href="/" on:click|preventDefault={() => toggleMobileNav(8)}>Neptune</a>
				</div>
				<img src={IconChevron} alt="selector" />
			</li>
		</div>
	{/if}
</nav>
