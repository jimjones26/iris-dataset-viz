<script lang="ts">
	import { getContext } from 'svelte';
	import * as d3 from 'd3';
	import type { IrisItem } from '$lib/stores/iris-interface';
	import Marks from '$lib/components/Marks.svelte';
	import AxisBottom from '$lib/components/AxisBottom.svelte';
	import AxisLeft from '$lib/components/AxisLeft.svelte';

	// grab the chart data from the store
	const chartData: any = getContext('csvData');

	// width, height and margins for svg container
	const width: number = 960;
	const height: number = 500;
	const margin = { top: 20, right: 30, bottom: 50, left: 220 };

	// inner height and width of chart
	const innerHeight = height - margin.top - margin.bottom;
	const innerWidth = width - margin.left - margin.right;

	// x and y axis values
	const xValue = (item: IrisItem) => item.sepal_length;
	const yValue = (item: IrisItem) => item.petal_width;

	// x and y scales
	const xScale = d3.scaleLinear().domain(<Iterable<number>>d3.extent($chartData, xValue));
	const yScale = d3
		.scaleLinear()
		.domain(<Iterable<number>>d3.extent($chartData, xValue))
		.range([0, innerHeight]);
</script>

<svg {width} {height}>
	<g transform={`translate(${margin.left}, ${margin.top})`}>
		<AxisBottom {xScale} {innerHeight} />
		<AxisLeft {yScale} />
		<Marks data={$chartData} {xScale} {yScale} {yValue} {xValue} /></g
	>
</svg>
