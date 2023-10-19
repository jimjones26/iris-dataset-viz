<script lang="ts">
	import { getContext } from 'svelte';

	const chartData: any = getContext('csvData');
</script>

{JSON.stringify($chartData)}
