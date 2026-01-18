<script lang="ts">
	import Cube from '$lib/components/cube.svelte';
</script>

<h1>Personal Website V3</h1>
<div class="polyhedraContainer">
	<Cube />
	<Cube />
	<Cube />
	<Cube />
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
