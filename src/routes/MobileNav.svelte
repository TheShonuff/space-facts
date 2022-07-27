<script lang="ts">
	import IconChevron from '../assests/icon-chevron.svg';
	export let menu = 1;
	export let open = false;
	export let toggleNav = (): void => {
		open = !open;
	};
	export function toggleMobileNav(num: number) {
		toggleNav();
		menu = num;
	}
</script>

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
