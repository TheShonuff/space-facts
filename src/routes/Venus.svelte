<script>
	import Venus from '../assests/planet-venus.svg';
	import VenusInternal from '../assests/planet-venus-internal.svg';
	import VenusGeo from '../assests/geology-venus.png';

	import Data from '../assests/data/data.json';
	let infoDisplay = 1;

	console.log(Data[1]);
</script>

<div class="container">
	<div class="main-content">
		<div class="planet-img">
			{#if infoDisplay === 1}
				<img src={Venus} alt="planet" />
			{:else if infoDisplay === 2}
				<img src={VenusInternal} alt="planet" />
			{:else if infoDisplay === 3}
				<img src={Venus} alt="planet" />
				<img class="planet-geo-img" src={VenusGeo} alt="planet geology" />
			{/if}
		</div>
		<div class="planet-facts-side">
			<h1>{Data[1].name}</h1>
			{#if infoDisplay === 1}
				<p>{Data[1].overview.content}</p>
				<p>Source</p>
			{:else if infoDisplay === 2}
				<p>{Data[1].structure.content}</p>
				<p>Source</p>
			{:else if infoDisplay === 3}
				<p>{Data[1].geology.content}</p>
				<p>Source</p>
			{/if}
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
		min-height: 400px;
		min-width: 400px;
		padding-left: 100px;
		padding-top: 50px;
	}

	.planet-geo-img {
		position: absolute;
		height: 199px;
		width: 163px;
		bottom: 0;
		left: 220px;
	}

	.planet-facts-side {
		display: flex;
		flex-direction: column;
		width: 350px;
		padding-left: 100px;
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
		font-size: 12px;
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
</style>
