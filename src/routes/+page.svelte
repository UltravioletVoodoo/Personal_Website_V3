<script lang="ts">
	import SideNav from '$lib/components/navigation/NavigationGroup.svelte';

	interface Point {
		x: number;
		y: number;
	}

	interface Vector extends Point {
		magnitude: string;
	}

	const rotateVector: Vector = { x: 0, y: 0, magnitude: '0deg' };

	function degreeify(x: number): string {
		return `${x}deg`;
	}

	function getMagnitude(p: Point) {
		const scaledPoint: Point = {
			x: p.x / (window.innerWidth / 2),
			y: p.y / (window.innerHeight / 2)
		};
		const unitMagnitude = Math.sqrt(Math.pow(scaledPoint.x, 2) + Math.pow(scaledPoint.y, 2));
		const maxRotation = 15;
		return unitMagnitude * maxRotation;
	}

	function getVectorFromCenter(x: number, y: number): Vector {
		const center: Point = { x: window.innerWidth / 2, y: window.innerHeight / 2 };
		const diffPoint: Point = { x: center.x - x, y: center.y - y };

		return { y: diffPoint.x, x: diffPoint.y, magnitude: degreeify(getMagnitude(diffPoint)) };
	}

	function handleMouseMove(e: MouseEvent) {
		const { x, y, magnitude } = getVectorFromCenter(e.x, e.y);

		rotateVector.x = x;
		rotateVector.y = y;
		rotateVector.magnitude = magnitude;
	}
</script>

<svelte:window onmousemove={handleMouseMove} />

<div
	class="container"
	style="--rX: {rotateVector.x}; --rY: {rotateVector.y}; --rMag: {rotateVector.magnitude}; "
>
	<SideNav />
</div>

<style>
	.container {
		display: flex;
		flex-grow: 1;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		transform-style: preserve-3d;
		transform: rotate3d(var(--rX), var(--rY), 0, var(--rMag));
		background-color: black;
		box-shadow: inset 0 0 300px -140px cyan;
		background: radial-gradient(cyan, black 1px, black);
		background-size: 14px 14px;
	}
</style>
