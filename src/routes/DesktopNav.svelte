<script lang="ts">
	import { menu } from './Stores';
</script>

<nav>
	<div class="background-nav">
		<div class="nav-container">
			<div class="page-title">
				<h2>Planet Facts</h2>
			</div>

			<ul id="menu">
				<li>
					<a href="/" on:click|preventDefault={() => menu.set(1)}>Mercury</a>
				</li>
				<li><a href="/" on:click|preventDefault={() => menu.set(2)}>Venus</a></li>
				<li><a href="/" on:click|preventDefault={() => menu.set(3)}>Earth</a></li>
				<li><a href="/" on:click|preventDefault={() => menu.set(4)}>Mars</a></li>
				<li><a href="/" on:click|preventDefault={() => menu.set(5)}>Jupiter</a></li>
				<li><a href="/" on:click|preventDefault={() => menu.set(6)}>Saturn</a></li>
				<li><a href="/" on:click|preventDefault={() => menu.set(7)}>Uranus</a></li>
				<li><a href="/" on:click|preventDefault={() => menu.set(8)}>Neptune</a></li>
			</ul>
		</div>
	</div>
</nav>

<style>
	.background-nav {
		background-color: #070724;
		background-image: url(/src/assests/background-stars.svg);
		height: 100%;
		width: 100%;
	}
</style>
