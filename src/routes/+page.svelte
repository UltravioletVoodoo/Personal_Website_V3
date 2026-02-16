<script lang="ts">
	import D4 from '$lib/components/d4.svelte';
</script>

<h1>Personal Website V3</h1>
<div class="polyhedraContainer">
	<D4 />
	<D4 />
	<D4 />
	<D4 />
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
