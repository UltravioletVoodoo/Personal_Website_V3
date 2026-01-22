<div class="container">
	<div class="d4">
		<div class="face one">1</div>
	</div>
</div>

<style>
	:root {
		/*Root Variable. All other values derived from this variable*/
		--containerSize: 1000px;

		/*True triangle vars*/
		--edgeLength: calc(var(--containerSize) / 2);
		--halfEdgeLength: calc(var(--edgeLength) / 2);
		--triangleHeight: calc(var(--edgeLength) * sqrt(3) / 2);
		--borderWidth: calc(var(--edgeLength) / 50);

		/*Inner triangle vars*/
		--innerTriangleEdgeLength: calc(var(--edgeLength) - var(--borderWidth) * 2);
		--innerTriangleHalfEdgeLength: calc(var(--innerTriangleEdgeLength) / 2);
		--innerTriangleHeight: calc(var(--innerTriangleEdgeLength) * sqrt(3) / 2);
	}

	@keyframes spin {
		from {
			transform: rotate3d(0, 0, 0, 0);
		}
		to {
			transform: rotate3d(0, 0, 1, 360deg);
		}
	}

	.container {
		width: var(--containerSize);
		height: var(--containerSize);
		border: 1px solid green;
	}
	.d4 {
		animation-name: spin;
		animation-timing-function: linear;
		animation-iteration-count: infinite;
		animation-duration: 100s;
		border: 1px solid green;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.face {
		position: relative;
		bottom: calc((var(--edgeLength) - var(--triangleHeight)) / 2);
		width: var(--edgeLength);
		height: var(--edgeLength);
		background-color: red;
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
		background-color: blue;
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
		content: '1';
		position: absolute;
		font-size: calc(var(--innerTriangleEdgeLength) / 4);
		font-weight: bold;
		color: red;
		top: calc(var(--innerTriangleEdgeLength) / 1.8);
	}
</style>
