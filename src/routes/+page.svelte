<script lang="ts">
	import Header from './Header.svelte';
</script>

<Header />

<style>
	/* Css Resets */
	:global(*) {
		box-sizing: border-box;
		padding: 0;
		margin: 0;
		background-repeat: no-repeat;
	}

	:global(*::after, *::before) {
		text-decoration: inherit;
		vertical-align: inherit;
	}

	:global(:hover) {
		outline: none;
	}

	:global(input) {
		border-radius: 0;
	}

	:global(form) {
		font: inherit;
	}

	:global(button) {
		cursor: pointer;
	}

	:global(a) {
		color: inherit;
		text-decoration: none;
	}

	/* Short Font Style */
	/* .code-text {
        font-family: monospace, sans-serif;
    } */

	:global(html) {
		font-size: 62.5%;
		tab-size: 4;
	}

	:global(body) {
		font-size: 2rem;
	}
</style>
