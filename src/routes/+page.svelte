<script lang="ts">
	import D4 from '$lib/components/d4.svelte';
	import D6 from '$lib/components/d6.svelte';
	import D8 from '$lib/components/d8.svelte';
</script>

<h1>Personal Website V3</h1>
<div class="polyhedraContainer">
	<D4 />
	<D6 />
	<D8 />
</div>

<style>
	:root {
		--containerSize: 1000px;
	}
	.polyhedraContainer {
		display: flex;
		flex-wrap: wrap;
		border: 1px solid gray;
		gap: 1rem;
		padding: 1rem;
	}
</style>
