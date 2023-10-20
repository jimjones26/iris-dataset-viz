<script lang="ts">
	import type { IrisItem } from '$lib/stores/iris-interface';

	export let data: Array<IrisItem>;
	export let xScale: any;
	export let yScale: any;
	export let xValue: any;
	export let yValue: any;
</script>

{#each data as item, i}
	<circle cx={xScale(xValue(item))} cy={yScale(yValue(item))} r={10} fill="#137B80">
		<title>hover</title>
	</circle>
{/each}
