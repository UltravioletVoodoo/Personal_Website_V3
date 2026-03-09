<div class="container">
	<div class="d4">
		<div class="face one"></div>
		<div class="face two"></div>
		<div class="symmetry first">
			<div class="face two"></div>
		</div>
		<div class="symmetry second">
			<div class="face two"></div>
		</div>
	</div>
</div>

<style>
	@keyframes spin {
		from {
			transform: rotate3d(0, 0, 0, 0);
		}
		to {
			transform: rotate3d(1, 1, 1, 360deg);
		}
	}

	.container {
		/*Root Variable is --containerSize. All Properties should be derived*/
		--containerSize: min(60vw, 800px);

		/*True triangle vars*/
		--edgeLength: calc(var(--containerSize) / 1.3);
		--halfEdgeLength: calc(var(--edgeLength) / 2);
		--triangleHeight: calc(var(--edgeLength) * sqrt(3) / 2);
		--borderWidth: calc(var(--edgeLength) / 50);

		/*Inner triangle vars*/
		--innerTriangleEdgeLength: calc(var(--edgeLength) - var(--borderWidth) * 2);
		--innerTriangleHalfEdgeLength: calc(var(--innerTriangleEdgeLength) / 2);
		--innerTriangleHeight: calc(var(--innerTriangleEdgeLength) * sqrt(3) / 2);

		/*Tetrahedral vars*/
		--faceToCenterDistance: calc(var(--edgeLength) * ((sqrt(8) / sqrt(12)) / 4));

		width: var(--containerSize);
		height: var(--containerSize);
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.d4 {
		animation-name: spin;
		animation-timing-function: linear;
		animation-iteration-count: infinite;
		animation-duration: 10s;
		width: 0px;
		height: 0px;
		transform-style: preserve-3d;
	}
	.symmetry {
		transform-style: preserve-3d;
	}
	.first {
		transform: rotateZ(120deg);
	}
	.second {
		transform: rotateZ(-120deg);
	}
	.face {
		opacity: 0.3;
		position: absolute;
		left: calc(var(--edgeLength) / -2);
		top: calc(var(--edgeLength) * (1 - (1 / (2 * sqrt(3)))) * -1);
		width: var(--edgeLength);
		height: var(--edgeLength);
		background-color: var(--accentColor);
		display: flex;
		align-items: center;
		justify-content: center;
		clip-path: polygon(
			0% var(--edgeLength),
			var(--halfEdgeLength) calc(100% - var(--triangleHeight)),
			var(--edgeLength) var(--edgeLength),
			0% var(--edgeLength)
		);
	}
	.face::before {
		content: '';
		position: absolute;
		top: calc(var(--borderWidth) * sqrt(2));
		left: var(--borderWidth);
		width: var(--innerTriangleEdgeLength);
		height: var(--innerTriangleEdgeLength);
		background-color: var(--primaryColor);
		display: flex;
		align-items: center;
		justify-content: center;
		clip-path: polygon(
			0% var(--innerTriangleEdgeLength),
			var(--innerTriangleHalfEdgeLength) calc(100% - var(--innerTriangleHeight)),
			var(--innerTriangleEdgeLength) var(--innerTriangleEdgeLength),
			0% var(--innerTriangleEdgeLength)
		);
		transform-origin: center;
	}
	.face::after {
		content: '';
		position: absolute;
		font-size: calc(var(--innerTriangleEdgeLength) / 4);
		font-weight: bold;
		color: red;
		top: calc(var(--innerTriangleEdgeLength) / 1.8);
	}
	.one {
		transform: translateZ(var(--faceToCenterDistance));
	}
	.two {
		transform-origin: calc(var(--halfEdgeLength) * 1) calc(var(--edgeLength) * ((6 - sqrt(3)) / 6))
			calc(var(--faceToCenterDistance) * -1);
		transform: translateZ(var(--faceToCenterDistance)) rotateX(-109deg) rotateY(0deg) rotateZ(60deg);
	}
</style>
