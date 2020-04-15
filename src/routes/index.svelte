<style>
	h1, figure, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2.8em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

	figure {
		margin: 0 0 1em 0;
	}

	img {
		width: 100%;
		max-width: 400px;
		margin: 0 0 1em 0;
	}

	p {
		margin: 1em auto;
	}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>

<script>
import { onMount } from 'svelte'
const staticData = import('./_data.js')

const dynamicDataPath = './_data.js'
const dynamicData = {
	data: import(dynamicDataPath)
}

</script>

<svelte:head>
	<title>Sapper project template</title>
</svelte:head>

<h1>Great success!</h1>

<figure>
	<img alt='Borat' src='great-success.png'>
	<figcaption>HIGH FIVE!</figcaption>
</figure>

<p><strong>Try editing this file (src/routes/index.svelte) to test live reloading.</strong></p>

<b>Top level dynamic import:</b>
{#await staticData}
Loading data...
{:then loaded}
{loaded.default}
{/await}

<br />

<b>Nested dynamic import</b>
{#await dynamicData.data}
Loading data...
{:then loaded}
{loaded.default}
{:catch error}
{error}
{/await}