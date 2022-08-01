<script lang="ts">
	import { menu, screenwidth } from './Stores';

	import Data from '../assets/data/data.json';
	let infoDisplay = 1;
	let selection: number;

	menu.subscribe((value) => {
		selection = value - 1;
	});

	console.log(Data[1]);

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
			<div class="planet-facts-selector" style="--selector-color:{colors[selection]}">
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
			<h5>{$screenwidth > 900 ? 'AVERAGE TEMPERATURE' : 'AVERAGE TEMP'}</h5>
			<h2>{Data[selection].temperature}</h2>
		</div>
	</div>
</div>

<style>
	.container {
		margin: 0 auto;
		padding-left: 165px;
		padding-right: 165px;
		padding-top: 100px;
		max-width: 1200px;
		min-width: 960px;
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
		background-color: var(--selector-color);
		border: var(--selector-color);
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
		max-width: 1200px;
		min-width: 950px;
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

	@media (max-width: 900px) {
		.container {
			padding: 0;
			max-width: 900px;
			min-width: 601px;
		}
		.main-content {
			flex-direction: column;
			width: 95%;
		}

		.planet-facts-side {
			flex-direction: row;
			width: 95%;
			align-items: center;
			justify-content: space-between;
			margin: 0 auto;
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
			padding-bottom: 50px;
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

		.planet-facts-body {
			height: 200px;
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

		.planet-stats-bottom {
			width: 90%;
			max-width: 900px;
			min-width: 601px;
			margin: 0 auto;
			justify-content: space-between;
		}
	}
</style>
