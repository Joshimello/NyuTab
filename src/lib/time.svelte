<script>
	let date = new Date()
	setInterval(() => {date = new Date()}, 1000)
	$: time = date.toLocaleTimeString("en-US", { hour12: false })
</script>

<main>
	{time}
</main>

<style>
	main {
		font-size: 2rem;
		font-family: monospace;
		letter-spacing: 0.75rem;
		color: rgba(255, 255, 255, 0.9);
	}
</style>