<script lang="ts">
	import D4 from './D4.svelte';
	import TextContent from './TextContent.svelte';

	const { selectedIndex }: { selectedIndex: number } = $props();
</script>

<div>
	{#if selectedIndex === 0}
		<D4 />
	{:else}
		<TextContent title="About Me" content="My name is Jonathan Bezeau and..." />
	{/if}
</div>

<style>
	div {
		display: flex;
		flex-grow: 1;
		justify-content: center;
	}
</style>
