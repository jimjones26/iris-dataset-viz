<script lang="ts">
	import type { LayoutData } from './$types';
	import * as d3 from 'd3';
	import { dataStore } from '$lib/stores/data-store';
	import { setContext } from 'svelte';

	export let data: LayoutData;

	let parsedData = d3.csvParse(data.data, d3.autoType);

	$: dataStore.set(parsedData);

	setContext('csvData', dataStore);
</script>

<slot />
