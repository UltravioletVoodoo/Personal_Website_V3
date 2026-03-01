<script lang="ts">
	import Polyhedra from '$lib/components/Polyhedra.svelte';
</script>

<div class="container">
	<div class="header">header</div>
	<div class="body">
		<Polyhedra />
	</div>
	<div class="footer">footer</div>
</div>

<style>
	:root {
		--containerSize: 10vw;
	}
	.container {
		display: flex;
		flex-grow: 1;
		flex-direction: column;
		align-items: center;
		justify-content: space-between;
	}
	.header {
	}
	.body {
	}
	.footer {
	}
</style>
