<script lang="ts">
	// import Venus from '../assests/planet-venus.svg';
	// import VenusInternal from '../assests/planet-venus-internal.svg';
	// import VenusGeo from '../assests/geology-venus.png';
	import { menu } from './Stores';

	import Data from '../assets/data/data.json';
	let infoDisplay = 1;
	let selection: number;

	menu.subscribe((value) => {
		selection = value - 1;
	});

	const colors = [
		'#419EBB',
		'#EDA249',
		'#6D2ED5',
		'#D14C32',
		'#D83A34',
		'#CD5120',
		'#1EC1A2',
		'#2D68F0'
	];

	console.log(Data[1]);
</script>

<div class="container">
	<div class="main-content">
		<div class="mobile-info-selection" style="--selector-color:{colors[selection]}">
			<div class={infoDisplay === 1 ? 'btn-selected' : 'btn'} on:click={() => (infoDisplay = 1)}>
				<p>OVERVIEW</p>
			</div>
			<div class={infoDisplay === 2 ? 'btn-selected' : 'btn'} on:click={() => (infoDisplay = 2)}>
				<p>STRUCTURE</p>
			</div>
			<div class={infoDisplay === 3 ? 'btn-selected' : 'btn'} on:click={() => (infoDisplay = 3)}>
				<p>SURFACE</p>
			</div>
		</div>

		<div class="planet-img">
			{#if infoDisplay === 1}
				<img src={`${Data[selection].images.planet}`} alt="planet" />
			{:else if infoDisplay === 2}
				<img src={Data[selection].images.internal} alt="planet" />
			{:else if infoDisplay === 3}
				<!-- <img src={Data[selection].images.planet} alt="planet" /> -->
				<img class="planet-geo-img" src={Data[selection].images.geology} alt="planet geology" />
			{/if}
		</div>
		<div class="planet-information">
			<h1>{Data[selection].name}</h1>
			{#if infoDisplay === 1}
				<p>{Data[selection].overview.content}</p>
				<p>Source</p>
			{:else if infoDisplay === 2}
				<p>{Data[selection].structure.content}</p>
				<p>Source</p>
			{:else if infoDisplay === 3}
				<p>{Data[selection].geology.content}</p>
				<p>Source</p>
			{/if}
		</div>
	</div>
	<div class="planet-stats-bottom">
		<div class="rotational box">
			<h5>ROTATION TIME</h5>
			<h2>{Data[selection].rotation}</h2>
		</div>
		<div class="revolution box">
			<h5>REVOLUTION TIME</h5>
			<h2>{Data[selection].revolution}</h2>
		</div>
		<div class="radius box">
			<h5>RADIUS</h5>
			<h2>{Data[selection].radius}</h2>
		</div>
		<div class="average-temp box">
			<h5>AVERAGE TEMPERATURE</h5>
			<h2>{Data[selection].temperature}</h2>
		</div>
	</div>
</div>

<style>
	.container {
		margin: 0 auto;
		width: 100vw;
	}
	.main-content {
		display: flex;
		flex-direction: column;
	}
	.planet-img {
		display: flex;
		justify-content: center;
		width: 100vw;
		margin: 0 auto;
		padding-top: 40px;
		padding-bottom: 40px;
	}
	.planet-img img {
		height: 176px;
		width: 176px;
		margin: 0 auto;
	}

	.mobile-info-selection {
		display: flex;
		flex-direction: row;
		justify-content: space-evenly;
		width: 100%;
		margin-right: 10px;
		padding-top: 10px;
		border-bottom: thin solid rgba(255, 255, 255, 0.5);
	}

	.btn {
		display: flex;
		flex-direction: row;
		background-color: transparent;
		cursor: pointer;
		color: white;
		letter-spacing: 2px;
		padding-bottom: 10px;
		border: rgba(255, 255, 255, 0.5);
	}
	.btn p {
		padding-left: 9px;
		font-family: 'League Spartan', sans-serif;
		font-size: 9px;
		line-height: 10px;
		font-weight: 700;
		font-style: normal;
		opacity: 0.5;
	}

	.btn-selected p {
		padding-left: 9px;
		font-family: 'League Spartan', sans-serif;
		font-size: 9px;
		line-height: 10px;
		font-weight: 700;
		font-style: normal;
		letter-spacing: 2px;
		color: white;
		opacity: 0.8;
	}

	.btn-selected {
		display: flex;
		flex-direction: row;
		border-bottom: 4px solid var(--selector-color);

		cursor: pointer;
	}

	.planet-information {
		margin-left: 10px;
		margin-right: 20px;
		justify-content: center;
		display: flex;
		flex-direction: column;
		width: 80%;
		margin: 0 auto;
	}

	.planet-information h1 {
		font-family: 'Antonio', sans-serif;
		font-weight: 400;
		font-size: 40px;
		text-align: center;
	}

	.planet-information p {
		text-align: center;
		font-family: 'League Spartan', sans-serif;
		font-style: normal;
		font-weight: 400;
		font-size: 11px;
		color: white;
		line-height: 22px;
	}

	.planet-geo-img {
		display: absolute;
		left: 0;
	}

	.planet-stats-bottom {
		width: 327px;
		margin: 0 auto;
	}

	.box {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		height: 48px;
		width: 327px;
		margin-top: 5px;

		border: rgba(255, 255, 255, 0.5);
		border-width: thin;
		margin-bottom: 16px;
		border-style: solid;
		font-family: 'League Spartan', sans-serif;
		font-style: normal;
		color: white;
	}

	.box h5 {
		opacity: 0.5;
		font-size: 8px;
		line-height: 25px;
		padding: 0;
		padding-left: 23px;
		color: white;
	}

	.box h2 {
		font-size: 20px;
		line-height: 26px;
		letter-spacing: -1.5px;
		padding-right: 20px;
		margin: 0;
	}
</style>
