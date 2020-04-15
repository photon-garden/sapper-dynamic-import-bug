<script>
const topLevelData = import('./_data.js')

const dataPath = './_data.js'
const nestedData = {
	data: import(dataPath)
}
</script>
<b>Top level dynamic import:</b>
{#await topLevelData}
Loading data...
{:then loaded}
{loaded.default}
{:catch error}
{error}
{/await}

<br />

<b>Nested dynamic import</b>
{#await nestedData.data}
Loading data...
{:then loaded}
{loaded.default}
{:catch error}
{error}
{/await}