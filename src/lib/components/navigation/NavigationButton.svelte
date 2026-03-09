<script lang="ts">
	interface NavigationButtonProps {
		title: string;
		selected: boolean;
		selectSelf: () => void;
	}

	const { title, selected, selectSelf }: NavigationButtonProps = $props();
</script>

<button onclick={selectSelf} class={selected ? 'selected' : undefined}>{title}</button>

<style>
	button {
		background-color: var(--primaryColor);
		transform: skewX(-20deg);
		border: none;
		color: black;
		height: 50px;
		font-size: 24px;
		font-weight: bold;
		cursor: pointer;
	}
	button:hover {
		background-color: var(--primaryColorSecondary);
	}
	button.selected {
		background-color: var(--secondaryColor);
	}
</style>
