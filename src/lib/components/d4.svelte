<script lang="ts">
	const containerSize = 500;
	const containerSizeStyle = `${containerSize}px`;
	const edgeLengthStyle = `${containerSize / 2}px`;
</script>

<div
	class="container"
	style="--containerSize: {containerSizeStyle}; --edgeLength: {edgeLengthStyle}"
>
	<div class="d4">
		<div class="faceContainer one">
			<div class="facePanel"></div>
		</div>
		<div class="faceContainer two">
			<div class="facePanel"></div>
		</div>
		<!-- <div class="face two">2</div>
        <div class="face three">3</div>
        <div class="face four">4</div> -->
	</div>
</div>

<style>
	@keyframes spin {
		from {
			transform: rotate3d(0, 0, 0, 0);
		}
		to {
			transform: rotate3d(4, 3, 1, 360deg);
		}
	}

	.container {
		border: 1px solid green;
		width: var(--containerSize);
		height: var(--containerSize);
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.d4 {
		transform-style: preserve-3d;
		border: 5px solid orange;
		transform: rotate3d(1, 1, 0, 45deg);
		animation-name: spin;
		animation-timing-function: linear;
		animation-iteration-count: infinite;
		animation-duration: 10s;
	}
	.faceContainer {
		width: var(--edgeLength);
		height: calc(var(--edgeLength) * sqrt(3) / 2);
		position: absolute;
		display: flex;
		justify-content: center;
	}
	.facePanel {
		opacity: 0.5;
		width: 0;
		height: 0;
		border-top: unset;
		border-right: calc((var(--edgeLength) + 10px) / 2) solid transparent;
		border-bottom: calc((var(--edgeLength) + 10px) * sqrt(3) / 2) solid green;
		border-left: calc((var(--edgeLength) + 10px) / 2) solid transparent;
	}
	.facePanel::before {
		content: '';
		width: 0;
		height: 0;
		position: absolute;
		left: 0;
		border-top: unset;
		border-right: calc(var(--edgeLength) / 2) solid transparent;
		border-bottom: calc(var(--edgeLength) * sqrt(3) / 2) solid purple;
		border-left: calc(var(--edgeLength) / 2) solid transparent;
		top: 6px;
	}
	.facePanel::after {
		content: '1';
		position: absolute;
		font-size: 64px;
		font-weight: bold;
		top: calc(var(--edgeLength) * sqrt(3) / 4);
		left: calc(var(--edgeLength) / 2 - 16px);
	}
	.one {
		transform: translateZ(calc(var(--edgeLength) * sqrt(3) / 2));
	}
</style>
