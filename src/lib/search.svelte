<script>
	import { fade } from 'svelte/transition'
	let input
</script>

<main>
	<form on:submit|preventDefault={window.location.replace(`https://google.com/search?q=${input}`)}>
		<input in:fade={{ delay: 1000 }} bind:value={input} />
	</form>
</main>

<style>
	input {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -70%);
		font-size: 1.5rem;
		padding: 0.5rem 1rem;
		border-radius: 2rem;
		background: rgba(255, 255, 255, 0.8);
		border: 0.1rem solid rgba(255, 255, 255, 0.9);
		text-align: center;
		color: #2A3441;
		font-family: monospace;
		letter-spacing: 0.2rem;
		text-transform: uppercase;
	}

	input:focus {
		outline: none;
	}
</style>