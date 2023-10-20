<script lang="ts">
	export let yScale: any;
</script>

{#each yScale.domain() as tick, i}
	<text fill="#635F5D" style="text-anchor: end;" dy=".32em" x={-3} y={yScale(tick)}>{tick}</text>
{/each}
