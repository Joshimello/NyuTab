<script>
	let imageUrl = new Promise(resolve => {
		fetch('http://colormind.io/api/', ({
			method: 'POST',
			body: JSON.stringify({model: "ui"})
		}))
		.then(res => res.json())
		.then(url => resolve(url))
	})

	let date = new Date()
	setInterval(() => {date = new Date()}, 1000)
	$: time = date.toLocaleTimeString("en-US", { hour12: false })
</script>

<main>
	{#await imageUrl}
	<span>uwu</span>
	{:then data}
	<section>
		<span>{time}</span>
		<div>
			{#each data.result as color}
			<div style="background: rgba({color[0]}, {color[1]}, {color[2]}, 1);"></div>
			{/each}
		</div>
		<span>コーヒーがほしい</span>
	</section>
	{/await}
</main>

<style>
	main {
		height: 100vh;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		background: #2A3441;
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

	section > span:nth-child(1) {
		font-size: 2rem;
		font-family: monospace;
		letter-spacing: 0.75rem;
		color: rgba(255, 255, 255, 0.9);
	}

	section > span:nth-child(3) {
		font-size: 2rem;
		color: rgba(255, 255, 255, 0.9);
		align-self: end;
	}

	section > div {
		height: 250px;
		width: 400px;
		display: flex;
		border:	solid 5px rgba(255, 255, 255, 0.9);
	}

	div > div {
		height: 100%;
		flex-grow: 1;
	}
</style>