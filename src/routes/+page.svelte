<script lang="ts">
	import Cube from '$lib/components/cube.svelte';
	import D4 from '$lib/components/d4.svelte';
	import D6 from '$lib/components/d6.svelte';
</script>

<h1>Personal Website V3</h1>
<div class="polyhedraContainer">
	<Cube />
	<D4 />
	<D6 />
</div>

<style>
	.polyhedraContainer {
		display: flex;
		flex-wrap: wrap;
		border: 1px solid gray;
		gap: 1rem;
		padding: 1rem;
	}
</style>
