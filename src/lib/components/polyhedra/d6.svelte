<div class="container">
	<div class="d6">
		<div class="face"></div>
		<div class="symmetry first">
			<div class="face"></div>
		</div>
		<div class="symmetry second">
			<div class="face"></div>
		</div>
		<div class="symmetry third">
			<div class="face"></div>
		</div>
		<div class="symmetry fourth">
			<div class="face"></div>
		</div>
		<div class="symmetry fifth">
			<div class="face"></div>
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
		--edgeLength: calc(var(--containerSize) / 2);
		--halfEdgeLength: calc(var(--edgeLength) / 2);

		width: var(--containerSize);
		height: var(--containerSize);
		border: 1px solid green;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.d6 {
		animation-name: spin;
		animation-timing-function: linear;
		animation-iteration-count: infinite;
		animation-duration: 10s;
		width: 0px;
		height: 0px;
		transform-style: preserve-3d;
	}
	.face {
		opacity: 0.7;
		position: absolute;
		outline-width: calc(var(--edgeLength) / 50); /*TODO: this border looks weird*/
		outline-color: blue;
		outline-style: solid;
		width: var(--edgeLength);
		height: var(--edgeLength);
		background-color: pink;
		transform: translate3d(
			calc(var(--halfEdgeLength) * -1),
			calc(var(--halfEdgeLength) * -1),
			var(--halfEdgeLength)
		);
	}
	.symmetry {
		transform-style: preserve-3d;
		transform-origin: var(--halfEdgeLength), var(--halfEdgeLength), var(--halfEdgeLength);
	}
	.first {
		transform: rotateX(90deg);
	}
	.second {
		transform: rotateX(180deg);
	}
	.third {
		transform: rotateX(270deg);
	}
	.fourth {
		transform: rotateY(90deg);
	}
	.fifth {
		transform: rotateY(270deg);
	}
</style>
