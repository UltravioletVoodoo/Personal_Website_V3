<script lang="ts">
	interface AnimationProps {
		x: number;
		y: number;
		z: number;
		duration: number;
	}

	const sideLength = 200;
	const sideLengthStyle = `${sideLength}px`;

	let animationProps: AnimationProps = { x: 1, y: 1, z: 0, duration: 5 };

	function getRandomInt(min: number, max: number) {
		const minCeiled = Math.ceil(min);
		const maxFloored = Math.floor(max);
		return Math.floor(Math.random() * (maxFloored - minCeiled) + minCeiled); // The maximum is exclusive and the minimum is inclusive
	}

	function nudgeRandomly(value: number, min: number, max: number) {
		const dx = 1;
		const shouldRaise = getRandomInt(0, 2) === 1;
		return shouldRaise ? Math.min(value + dx, max) : Math.max(value - dx, min);
	}

	function getAnimationValues(): AnimationProps {
		return {
			x: nudgeRandomly(animationProps.x, 1, 10),
			y: nudgeRandomly(animationProps.y, 1, 10),
			z: nudgeRandomly(animationProps.z, 1, 10),
			duration: nudgeRandomly(animationProps.duration, 2, 10)
		};
	}

	function recalculateAnimation() {
		animationProps = getAnimationValues();
	}

	setInterval(recalculateAnimation, 500);
</script>

<div
	class="container"
	style="--sideLength: {sideLengthStyle}; --vectorX: {animationProps.x}; --vectorY: {animationProps.y}; --vectorZ: {animationProps.z}; --duration: {`${animationProps.duration}s`}"
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
		animation-duration: var(--duration);
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
	.face:hover {
		background-color: red;
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
