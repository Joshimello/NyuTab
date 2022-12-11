<script>
	const themes = {
		'MorningFog':     ['#AAB0B6', '#DDDFE2'],
		'IcyMint':        ['#84B6C0', '#CAE0E4'],
		'IslandGetaway':  ['#47A5AB', '#73D1D3'],
		'CoolBreeze':     ['#699DC0', '#A7C6DB'],
		'SilkyPink':      ['#D5B2AC', '#F0E3E1'],
		'BubbleGum':      ['#F46FA1', '#F9BCD3'],
		'SunnyDay':       ['#D3AD3C', '#EDE1BA'],
		'MangoParadise':  ['#E48E30', '#F1CBA0'],
		'DarkStormy':     ['#38393C', '#56585D'],
		'CoolStale':      ['#2B3441', '#46546A'],
		'MoonlightGlow':  ['#0F2B48', '#1C4C7F'],
		'JuicyPlum':      ['#452372', '#6C36B1'],
		'SpicyRed':       ['#6A0D12', '#A2131D'],
		'MysticalForest': ['#143E1D', '#20612D']
	}

	let selectedTheme = 'CoolStale', open = false

	$: bgColor = themes[selectedTheme][0]

	export let bgColor
</script>

<main>
	{#if open}
	<input type="text" style="background: {themes[selectedTheme][0]}" bind:value={selectedTheme}>
	{/if}
	<button on:click={() => {open = !open}}>···</button>
</main>

<style>
	main {
		width: 100%;
		position: absolute;
		padding: 0rem 0.5rem;
		box-sizing: border-box;
		bottom: 0;
		display: flex;
		align-items: center;
	}

	button {
		color: rgba(255, 255, 255, 0.9);
		background: transparent;
		border: none;
		font-size: 2rem;
		transition: 0.1s;
	}

	button:hover {
		transform: scaleX(1.2);
	}

	input {
		font-size: 1.5rem;
		border: rgba(255, 255, 255, 0.9) 0.1rem solid;
	}
</style>