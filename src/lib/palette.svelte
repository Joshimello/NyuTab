<script>
	import { fade } from 'svelte/transition'
	export let colors
</script>

<main>
	{#each colors.result as color, i}
	<div in:fade={{ delay: 200+50*i }} style="background: rgba({color[0]}, {color[1]}, {color[2]}, 1);"></div>
	{/each}
</main>

<style>
	main {
		height: 250px;
		width: 400px;
		display: flex;
		border:	solid 5px rgba(255, 255, 255, 0.9);
	}

	div {
		height: 100%;
		flex-grow: 1;
	}
</style>