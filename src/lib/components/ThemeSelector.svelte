<script lang="ts">
	import { onMount } from 'svelte';

	let theme = 'dark';

	function toggleTheme() {
		theme = theme === 'dark' ? 'light' : 'dark';
		document.documentElement.setAttribute('theme', theme);
	}

	onMount(() => {
		document.documentElement.setAttribute('theme', theme);
	});
</script>

<button onclick={toggleTheme}>{theme === 'dark' ? 'Light' : 'Dark'} Mode</button>

<style>
	:root {
		--primaryColor: cyan;
		--primaryColorSecondary: cadetblue;
		--secondaryColor: brown;
		--accentColor: burlywood;
		--backgroundColor: black;
		--otherBackgroundColor: white;
	}
	:root[theme='light'] {
		--primaryColor: darkgreen;
		--primaryColorSecondary: green;
		--secondaryColor: mediumslateblue;
		--accentColor: coral;
		--backgroundColor: white;
		--otherBackgroundColor: black;
	}
	button {
		position: fixed;
		top: 50px;
		right: 50px;
		height: 100px;
		width: 100px;
		border-radius: 100%;
		background-color: var(--primaryColor);
		color: var(--backgroundColor);
		border: 5px solid var(--secondaryColor);
		opacity: 0.5;
		cursor: pointer;
		font-size: 24px;
		font-weight: bold;
	}
	button:hover {
		opacity: 1;
	}
</style>
