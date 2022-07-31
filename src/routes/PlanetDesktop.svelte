<script lang="ts">
	// import Venus from '../assests/planet-venus.svg';
	// import VenusInternal from '../assests/planet-venus-internal.svg';
	// import VenusGeo from '../assests/geology-venus.png';
	import { menu } from './Stores';
	import { fade } from 'svelte/transition';

	import Data from '../assets/data/data.json';
	let infoDisplay = 1;
	let selection: number;

	menu.subscribe((value) => {
		selection = value - 1;
	});

	console.log(Data[1]);
</script>

<div class="container">
	<div class="main-content">
		<div class="planet-img">
			{#if infoDisplay === 1}
				<img src={`${Data[selection].images.planet}`} alt="planet" />
			{:else if infoDisplay === 2}
				<img src={Data[selection].images.internal} alt="planet" />
			{:else if infoDisplay === 3}
				<img src={Data[selection].images.planet} alt="planet" />
				<img class="planet-geo-img" src={Data[selection].images.geology} alt="planet geology" />
			{/if}
		</div>
		<div class="planet-facts-side">
			<div class="planet-facts-information">
				<h1>{Data[selection].name}</h1>
				<div class="planet-facts-body">
					{#if infoDisplay === 1}
						<p>{Data[selection].overview.content}</p>
						<div class="source">
							<p>Source :</p>
							<a href={Data[selection].overview.source}>Wikipedia</a>
							<img src="./assets/icon-source.svg" alt="link image" />
						</div>
					{:else if infoDisplay === 2}
						<p>{Data[selection].structure.content}</p>
						<div class="source">
							<p>Source :</p>
							<a href={Data[selection].overview.source}>Wikipedia</a>
							<img src="./assets/icon-source.svg" alt="link image" />
						</div>
					{:else if infoDisplay === 3}
						<p>{Data[selection].geology.content}</p>
						<div class="source">
							<p>Source :</p>
							<a href={Data[selection].overview.source}>Wikipedia</a>
							<img src="./assets/icon-source.svg" alt="link image" />
						</div>
					{/if}
				</div>
			</div>
			<div class="planet-facts-selector">
				<div class={infoDisplay === 1 ? 'btn-selected' : 'btn'} on:click={() => (infoDisplay = 1)}>
					<p>01</p>
					<p>OVERVIEW</p>
				</div>
				<div class={infoDisplay === 2 ? 'btn-selected' : 'btn'} on:click={() => (infoDisplay = 2)}>
					<p>02</p>
					<p>INTERNAL STRUCTURE</p>
				</div>
				<div class={infoDisplay === 3 ? 'btn-selected' : 'btn'} on:click={() => (infoDisplay = 3)}>
					<p>03</p>
					<p>SURFACE GEOLOGY</p>
				</div>
			</div>
		</div>
	</div>

	<div class="planet-stats-bottom">
		<div class="rotational box">
			<h5>ROTATION TIME</h5>
			<h2>{Data[1].rotation}</h2>
		</div>
		<div class="revolution box">
			<h5>REVOLUTION TIME</h5>
			<h2>{Data[1].revolution}</h2>
		</div>
		<div class="radius box">
			<h5>RADIUS</h5>
			<h2>{Data[1].radius}</h2>
		</div>
		<div class="average-temp box">
			<h5>AVERAGE TEMPERATURE</h5>
			<h2>{Data[1].temperature}</h2>
		</div>
	</div>
</div>

<style>
	.container {
		margin: 0 auto;
		padding-left: 165px;
		padding-right: 165px;
		padding-top: 100px;
	}
	.main-content {
		display: flex;
		justify-content: space-between;
		flex-direction: row;
		width: 100%;
		margin: 0 auto;
	}

	.planet-img {
		position: relative;
		display: inline;
		height: 400px;
		width: 400px;
		padding-left: 100px;
		padding-top: 50px;
	}

	.planet-img img {
		position: relative;
		height: 400px;
		width: 400px;
	}

	.planet-img .planet-geo-img {
		position: absolute;
		height: 199px;
		width: 163px;
		bottom: -70px;
		left: 220px;
	}

	.planet-facts-side {
		display: flex;
		flex-direction: column;
		width: 350px;
		padding-left: 100px;
	}

	.source {
		display: flex;
		flex-direction: row;
		align-items: center;
		font-family: 'League Spartan', sans-serif;
		font-size: 14px;
		line-height: 25px;
		font-style: normal;
	}
	.source p {
		opacity: 0.5;
	}
	.source a {
		text-transform: none;
		text-decoration: underline;
		opacity: 0.5;
		padding-left: 4px;
	}

	.source img {
		padding-left: 4px;
	}

	.btn {
		display: flex;
		flex-direction: row;
		height: 48px;
		width: 350px;
		background-color: transparent;
		cursor: pointer;
		color: white;
		border: rgba(255, 255, 255, 0.5);
		border-width: thin;
		margin-bottom: 16px;
		border-style: solid;
	}

	.btn-selected {
		display: flex;
		flex-direction: row;
		height: 48px;
		width: 350px;
		background-color: #eda249;
		border: rgba(237, 162, 73, 1);
		border-width: thin;
		margin-bottom: 16px;
		border-style: solid;
		cursor: pointer;
	}

	.btn-selected p {
		padding-left: 28px;
		font-family: 'League Spartan', sans-serif;
		font-size: 9px;
		line-height: 25px;
		font-style: normal;
	}

	.btn-selected p:first-child {
		opacity: 0.5;
	}
	.btn:hover {
		background-color: rgba(216, 216, 216, 0.2);
		border: rgba(216, 216, 216, 0.2);
		border-width: thin;
		margin-bottom: 16px;
		border-style: solid;
	}

	.btn p {
		padding-left: 28px;
		font-family: 'League Spartan', sans-serif;
		font-size: 12px;
		line-height: 25px;
		font-style: normal;
	}

	.btn p:first-child {
		opacity: 0.5;
	}
	.planet-facts-side p {
		font-family: 'League Spartan', sans-serif;
		font-style: normal;
		font-weight: 400;
		font-size: 15px;
		color: white;
		line-height: 25px;
	}

	.planet-facts-body {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		height: 250px;
		width: 350px;
		top: 0;
	}

	.planet-facts-side p:first-child {
		flex-wrap: nowrap;
	}

	.planet-facts-side h1 {
		font-family: 'Antonio', sans-serif;
		font-weight: 400;
		font-size: 80px;
		margin: 0;
	}

	.planet-stats-bottom {
		display: flex;
		justify-content: space-between;
	}
	.box {
		display: flex;
		flex-direction: column;
		height: 128px;
		width: 255px;
		margin-top: 67px;
		margin-left: 15px;
		margin-right: 15px;
		border: rgba(255, 255, 255, 0.5);
		border-width: thin;
		margin-bottom: 16px;
		border-style: solid;
		font-family: 'League Spartan', sans-serif;
		font-style: normal;
		color: white;
		padding-left: 23px;
	}

	.box h5 {
		opacity: 0.5;
		font-size: 11px;
		line-height: 25px;
		padding: 0;
		margin-top: 20px;
		margin-bottom: 8px;
	}

	.box h2 {
		font-size: 40px;
		line-height: 52px;
		letter-spacing: -1.5px;
		margin: 0;
	}

	.box:first-child {
		margin-left: 0;
	}

	.box:last-child {
		margin-right: 0;
	}

	@media (max-width: 820px) {
		.container {
			padding: 0;
		}
		.main-content {
			flex-direction: column;
		}

		.planet-facts-side {
			flex-direction: row;
			width: 100vw;
			align-items: center;
			justify-content: space-between;
			margin: 0;
			padding: 0;
		}

		.planet-facts-side h1 {
			font-size: 48px;
			line-height: 62px;
			text-transform: uppercase;
		}
		.planet-img {
			display: block;
			margin: 0 auto;
		}

		.planet-img img {
			height: 370px;
			width: 370px;
		}
		.planet-facts-selector {
			margin-right: 20px;
		}

		.planet-facts-information {
			margin-right: 60px;
			margin-left: 30px;
		}

		.planet-facts-information p {
			font-size: 12px;
			line-height: 22px;
		}
		.btn {
			width: 281px;
			height: 40px;
		}
		.planet-img .planet-geo-img {
			left: 205px;
			bottom: -25px;
		}

		.btn p {
			padding-left: 28px;
			font-family: 'League Spartan', sans-serif;
			font-size: 9px;
			line-height: 25px;
			letter-spacing: 2px;
			font-style: normal;
		}

		.btn-selected {
			width: 281px;
			height: 40px;
			display: flex;
			flex-direction: row;
			background-color: #d83a34;
			border: rgba(216, 58, 52, 1);
			border-width: thin;
			margin-bottom: 16px;
			border-style: solid;
			cursor: pointer;
		}

		.btn-selected p {
			font-size: 9px;
			line-height: 25px;
			letter-spacing: 2px;
		}
		.box {
			flex-direction: column;
			align-items: left;
			margin-top: 20px;
			width: 164px;
			height: 88px;
		}

		.box h2 {
			font-size: 24px;
			margin-bottom: 40px;
		}

		.box h5 {
			font-size: 11px;
			margin-bottom: 0;
			margin-top: 10px;
		}
	}
</style>
