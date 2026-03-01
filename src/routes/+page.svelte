<script lang="ts">
	import Polyhedra from '$lib/components/Polyhedra.svelte';

	let mouseXRotate = '0deg';
	let mouseYRotate = '0deg';

	function degreeify(v: number, totalV: number) {
		const center = totalV / 2;
		const distanceFromCenter = center - v;
		const ratioToEdge = distanceFromCenter / center;
		const deg = ratioToEdge * 50;

		return `${deg}deg`;
	}

	function handleMouseMove(e: MouseEvent) {
		mouseXRotate = degreeify(e.x, window.innerWidth);
		mouseYRotate = degreeify(e.y, window.innerHeight);
		console.log(`Position: (${e.x}, ${e.y})`);
	}
</script>

<svelte:window onmousemove={handleMouseMove} />

<div class="container" style="--mouseXRotate: {mouseXRotate}; --mouseYRotate: {mouseYRotate}">
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
		transform-style: preserve-3d;
		transform: rotateY(var(--mouseXRotate)) rotateX(var(--mouseYRotate));
		border: 1px solid green;
	}
	.header {
	}
	.body {
	}
	.footer {
	}
</style>
