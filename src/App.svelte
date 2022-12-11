<script>
	import { fade } from 'svelte/transition'
	import Time from './lib/time.svelte'
	import Text from './lib/text.svelte'
	import Search from './lib/search.svelte'
	import Palette from './lib/palette.svelte'
	import Background from './lib/background.svelte'

	let imageUrl = new Promise(resolve => {
		fetch('http://colormind.io/api/', ({
			method: 'POST',
			body: JSON.stringify({model: "ui"})
		}))
		.then(res => res.json())
		.then(url => resolve(url))
	})

	let show = false
	let bgColor
</script>

<main style="background: {bgColor};">
	{#await imageUrl}
	<span transition:fade
		on:introstart="{() => show = false}"
		on:outroend="{() => show = true}">nya...
	</span>
	{:then data}
		{#if show}
		<section in:fade>
			<Search/>
			<Time/>
			<Palette colors={data}/>
			<Text text="コーヒーがほしい"/>
		</section>
		{/if}
	{/await}
	<Background bind:bgColor={bgColor}/>
</main>

<style>
	main {
		height: 100vh;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	main > span {
		font-size: 2rem;
		font-family: monospace;
		letter-spacing: 0.75rem;
		color: rgba(255, 255, 255, 0.9);
	}

	section {
		display: flex;
		flex-direction: column;
	}
</style>