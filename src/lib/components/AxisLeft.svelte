<script lang="ts">
	export let yScale: any;
	export let innerWidth: number;
</script>

{#each yScale.ticks() as tick, i}
	<g transform={`translate(0, ${yScale(tick)})`}>
		<line x2={innerWidth} stroke="#C0C0BB" />
		<text fill="#635F5D" style="text-anchor: end;" dy=".32em" x={-3}>{tick}</text>
	</g>
{/each}
