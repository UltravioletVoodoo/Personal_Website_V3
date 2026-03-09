<script lang="ts">
	import AboutMe from './AboutMe.svelte';
	import D4 from './D4.svelte';
	import TextContent from './TextContent.svelte';

	const { selectedIndex }: { selectedIndex: number } = $props();
</script>

<div>
	{#if selectedIndex === 0}
		<D4 />
	{:else if selectedIndex === 1}
		<AboutMe />
	{:else if selectedIndex === 2}
		<TextContent title="Professional" content="I have lots of work experience..." />
	{:else if selectedIndex === 3}
		<TextContent title="Personal Projects" content="I like to make things..." />
	{/if}
</div>

<style>
	div {
		display: flex;
		flex-grow: 1;
		justify-content: center;
	}
</style>
