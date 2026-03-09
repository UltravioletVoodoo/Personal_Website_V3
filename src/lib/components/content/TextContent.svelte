<script lang="ts">
	interface TextContentProps {
		title: string;
		content: string;
	}

	const { title, content }: TextContentProps = $props();
</script>

<div>
	<h1>{title}</h1>
	<p>{content}</p>
</div>

<style>
	h1,
	p {
		color: var(--primaryColor);
	}
</style>
