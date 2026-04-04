<script lang="ts">
	import AboutMe from './AboutMe.svelte';
	import TextContent from './TextContent.svelte';

	const { selectedIndex }: { selectedIndex: number } = $props();
</script>

{#if selectedIndex !== 0}
	<div>
		{#if selectedIndex === 1}
			<AboutMe />
		{:else if selectedIndex === 2}
			<TextContent title="Professional" content="I have lots of work experience..." />
		{:else if selectedIndex === 3}
			<TextContent title="Personal Projects" content="I like to make things..." />
		{/if}
	</div>
{/if}

<style>
	div {
		display: flex;
		flex-grow: 1;
		justify-content: center;
		background-color: var(--backgroundColor);
		padding: 1rem;
		border-radius: 1rem;
		box-shadow: 0 0 150px 100px var(--backgroundColor);
	}
</style>
