<script lang="ts">
	interface RotationAxis {
		x: number;
		y: number;
		z: number;
	}

	const sideLength = 100;
	const sideLengthStyle = `${sideLength}px`;

	const rotationAxis: RotationAxis = {
		x: Math.random() * 10,
		y: Math.random() * 10,
		z: Math.random() * 10
	};
</script>

<div
	class="container"
	style="--sideLength: {sideLengthStyle}; --vectorX: {rotationAxis.x}; --vectorY: {rotationAxis.y}; --vectorZ: {rotationAxis.z}"
>
	<div class="cube">
		<div class="face one">1</div>
		<div class="face two">2</div>
		<div class="face three">3</div>
		<div class="face four">4</div>
		<div class="face five">5</div>
		<div class="face six">6</div>
	</div>
</div>

<style>
	@keyframes spin {
		from {
			transform: rotate3d(0, 0, 0, 0);
		}
		to {
			transform: rotate3d(var(--vectorX), var(--vectorY), var(--vectorZ), 360deg);
		}
	}

	.container {
		border: 1px solid green;
		width: calc(var(--sideLength) * sqrt(3));
		height: calc(var(--sideLength) * sqrt(3));
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.cube {
		transition: 0.5s;
		color: blue;
		font-size: 64px;
		font-weight: bold;
		transform-style: preserve-3d;
		border: 10px solid purple;
		border-radius: 100%;
		animation-name: spin;
		animation-timing-function: linear;
		animation-iteration-count: infinite;
		animation-duration: 10s;
		position: relative;
	}
	.face {
		opacity: 0.1;
		position: absolute;
		width: var(--sideLength);
		height: var(--sideLength);
		background-color: pink;
		border: 3px solid blue;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.one {
		transform: translate3d(
			calc(var(--sideLength) / -2),
			calc(var(--sideLength) / -2),
			calc(var(--sideLength) / -2)
		);
	}
	.two {
		transform: rotate(180deg)
			translate3d(
				calc(var(--sideLength) / 2),
				calc(var(--sideLength) / 2),
				calc(var(--sideLength) / 2)
			);
	}
	.three {
		transform: rotateX(90deg) translate3d(calc(var(--sideLength) / -2), 0, 0);
	}
	.four {
		transform: rotateX(-90deg)
			translate3d(calc(var(--sideLength) / -2), 0, calc(var(--sideLength) * -1));
	}
	.five {
		transform: rotateY(90deg) translate3d(0, calc(var(--sideLength) / -2), 0);
	}
	.six {
		transform: rotateY(-90deg) translate3d(0, calc(var(--sideLength) / -2), var(--sideLength));
	}
</style>
