<div class="container">
	<div class="d4">
		<div class="symmetry">
			<div class="face top"></div>
		</div>
		<div class="symmetry second">
			<div class="face top"></div>
		</div>
		<div class="symmetry third">
			<div class="face top"></div>
		</div>
		<div class="symmetry fourth">
			<div class="face top"></div>
		</div>
		<div class="symmetry">
			<div class="face bottom"></div>
		</div>
		<div class="symmetry second">
			<div class="face bottom"></div>
		</div>
		<div class="symmetry third">
			<div class="face bottom"></div>
		</div>
		<div class="symmetry fourth">
			<div class="face bottom"></div>
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

		/*True triangle vars*/
		--edgeLength: calc(var(--containerSize) / 1.7);
		--halfEdgeLength: calc(var(--edgeLength) / 2);
		--triangleHeight: calc(var(--edgeLength) * sqrt(3) / 2);
		--borderWidth: calc(var(--edgeLength) / 50);

		/*Inner triangle vars*/
		--innerTriangleEdgeLength: calc(var(--edgeLength) - var(--borderWidth) * 2);
		--innerTriangleHalfEdgeLength: calc(var(--innerTriangleEdgeLength) / 2);
		--innerTriangleHeight: calc(var(--innerTriangleEdgeLength) * sqrt(3) / 2);

		/*Transform vars*/
		--triangleCenterYOffset: calc(var(--edgeLength) * (1 - (1 / (2 * sqrt(3)))));

		width: var(--containerSize);
		height: var(--containerSize);
		border: 1px solid green;
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
	.face {
		opacity: 0.5;
		position: absolute;
		left: calc(var(--edgeLength) / -2);
		top: calc(var(--triangleCenterYOffset) * -1);
		width: var(--edgeLength);
		height: var(--edgeLength);
		background-color: blue;
		display: flex;
		align-items: center;
		justify-content: center;
		clip-path: polygon(
			0% var(--edgeLength),
			var(--halfEdgeLength) calc(100% - var(--triangleHeight)),
			var(--edgeLength) var(--edgeLength),
			0% var(--edgeLength)
		);
		transform-origin: var(--halfEdgeLength) var(--triangleCenterYOffset);
	}
	.face::before {
		content: '';
		position: absolute;
		top: calc(var(--borderWidth) * sqrt(2));
		left: var(--borderWidth);
		width: var(--innerTriangleEdgeLength);
		height: var(--innerTriangleEdgeLength);
		background-color: aqua;
		display: flex;
		align-items: center;
		justify-content: center;
		clip-path: polygon(
			0% var(--innerTriangleEdgeLength),
			var(--innerTriangleHalfEdgeLength) calc(100% - var(--innerTriangleHeight)),
			var(--innerTriangleEdgeLength) var(--innerTriangleEdgeLength),
			0% var(--innerTriangleEdgeLength)
		);
	}
	.face::after {
		content: '';
		position: absolute;
		font-size: calc(var(--innerTriangleEdgeLength) / 4);
		font-weight: bold;
		color: red;
		top: calc(var(--innerTriangleEdgeLength) / 1.8);
	}
	.top {
		transform: translateY(calc(var(--edgeLength) * 0.33))
			translateZ(calc(var(--edgeLength) * -0.228)) rotateX(atan(sqrt(2)));
		/**TODO: get a precise value here. This isnt good enough. Mathematically precise!*/
	}
	.bottom {
		transform: translateY(calc(var(--edgeLength) * 0.33))
			translateZ(calc(var(--edgeLength) * 0.228)) rotateX(calc(atan(sqrt(2)) * -1));
		/**TODO: get a precise value here. This isnt good enough. Mathematically precise!*/
	}
	.symmetry {
		transform-style: preserve-3d;
	}
	.second {
		transform: rotateZ(90deg);
	}
	.third {
		transform: rotateZ(180deg);
	}
	.fourth {
		transform: rotateZ(270deg);
	}
</style>
