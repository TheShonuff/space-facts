<script lang="ts">
	import { menu, screenwidth } from './Stores';
	import { imgSizes, colors } from './helpers';
	import { fade, fly } from 'svelte/transition';

	import Data from '../assets/data/data.json';
	import { transition_in } from 'svelte/internal';
	let infoDisplay = 1;
	let selection: number;

	menu.subscribe((value) => {
		selection = value - 1;
	});
	$: imgSize = $screenwidth < 900 ? imgSizes[selection].Tablet : imgSizes[selection].Desktop;
</script>

<svelte:head>
	<title>{Data[selection].name}</title>
</svelte:head>

<div class="container">
	<div class="main-content">
		<div class="planet-img" style="--planet-size:{imgSize}">
			{#key selection}
				{#if infoDisplay === 1}
					<div class="the-planet">
						<img
							transition:fade={{ duration: 500 }}
							style="height:{imgSize}px"
							src={Data[selection].images.planet}
							alt="planet"
						/>
					</div>
				{:else if infoDisplay === 2}
					<img style="height:{imgSize}px" src={Data[selection].images.internal} alt="planet" />
				{:else if infoDisplay === 3}
					<img style="height:{imgSize}px" src={Data[selection].images.planet} alt="planet" />
					<img class="planet-geo-img" src={Data[selection].images.geology} alt="planet geology" />
				{/if}
			{/key}
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
							<img src="./assets/icon-source.svg" alt="overview source link icon" />
						</div>
					{:else if infoDisplay === 2}
						<p>{Data[selection].structure.content}</p>
						<div class="source">
							<p>Source :</p>
							<a href={Data[selection].structure.source}>Wikipedia</a>
							<img src="./assets/icon-source.svg" alt="planet structure source link icon" />
						</div>
					{:else if infoDisplay === 3}
						<p>{Data[selection].geology.content}</p>
						<div class="source">
							<p>Source :</p>
							<a href={Data[selection].geology.source}>Wikipedia</a>
							<img src="./assets/icon-source.svg" alt="planet structure source link icon" />
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

<style src="../styles/planet-desktop.css"></style>
