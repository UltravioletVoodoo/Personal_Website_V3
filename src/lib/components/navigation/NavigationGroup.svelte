<script lang="ts">
	import ContentSelector from '../content/ContentSelector.svelte';
	import NavigationButton from './NavigationButton.svelte';

	let selectedIndex = $state(0);

	function handleSelect(newIndex: number) {
		selectedIndex = newIndex;
	}
</script>

<div class="container">
	<div class="content">
		<ContentSelector {selectedIndex} />
	</div>
	<div class="navigation">
		<NavigationButton
			title="Home"
			selected={selectedIndex === 0}
			selectSelf={() => handleSelect(0)}
		/>
		<NavigationButton
			title="About Me"
			selected={selectedIndex === 1}
			selectSelf={() => handleSelect(1)}
		/>
		<NavigationButton
			title="Professional"
			selected={selectedIndex === 2}
			selectSelf={() => handleSelect(2)}
		/>
		<NavigationButton
			title="Personal Projects"
			selected={selectedIndex === 3}
			selectSelf={() => handleSelect(3)}
		/>
	</div>
</div>

<style>
	.container {
		display: flex;
		flex-grow: 1;
		flex-direction: column;
		margin: 10rem 0;
		gap: 1rem;
		width: min(60vw, 800px);
	}
	.content {
		display: flex;
		flex-grow: 1;
		align-items: center;
	}
	.navigation {
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
	}
</style>
