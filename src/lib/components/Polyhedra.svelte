<script>
	import D4 from './polyhedra/d4.svelte';
	import D6 from './polyhedra/d6.svelte';
	import D8 from './polyhedra/d8.svelte';
</script>

<div class="container">
	<D4 />
	<D6 />
	<D8 />
	<D8 />
	<D8 />
	<D8 />
</div>

<style>
	.container {
		display: flex;
		flex-wrap: wrap;
		gap: 1rem;
		padding: 1rem;
		box-shadow: 0px 0px 50px 20px cadetblue;
		border-radius: 5rem;
		background-color: white;
		border: 5px solid cyan;
		background: radial-gradient(cyan, black 1px, transparent);
		background-size: 8px 8px;
	}
</style>
