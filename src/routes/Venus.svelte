<script>
	import Venus from '../assests/planet-venus.svg';

	import Data from '../assests/data/data.json';
	let infoDisplay = 1;

	console.log(Data[1]);
</script>

<div class="container">
	<div class="main-content">
		<img src={Venus} alt="planet" />
		<div class="planet-facts-side">
			<h1>Venus</h1>
			{#if infoDisplay === 1}
				<p>{Data[1].overview.content}</p>
			{:else if infoDisplay === 2}
				<p>{Data[1].structure.content}</p>
			{:else if infoDisplay === 3}
				<p>{Data[1].geology.content}</p>
			{/if}
			<button>overview</button>
			<button>internal structure</button>
			<button>Surface Geology</button>
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
		padding-top: 188px;
	}
	.main-content {
		display: flex;
		justify-content: space-between;
		flex-direction: row;
		width: 100%;
		margin: 0 auto;
	}

	.main-content img {
		height: 400px;
		width: 400px;
	}

	.planet-facts-side {
		display: flex;
		flex-direction: column;
		width: 350px;
	}

	.planet-facts-side p {
		font-family: 'League Spartan', sans-serif;
		font-weight: 400;
		font-size: 14px;
		color: white;
		line-height: 25px;
	}

	.planet-stats-bottom {
		display: flex;
	}
	.box {
		height: 128px;
		width: 255px;
	}
</style>
