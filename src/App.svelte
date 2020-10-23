<script>
	let your_ip = ""

	let user = { loggedIn: false}

	function toggle() {
		user.loggedIn = !user.loggedIn;
		your_ip = geoplugin_request()

	}
</script>

<main>
	{#if user.loggedIn}
		<h1>Hello, {your_ip}</h1>
		<button on:click={toggle}>
			click me
		</button>
		
	{/if}

	{#if !user.loggedIn}
		<h1>Hey 127.0.0.1</h1>
		<button on:click={toggle}>
			click me
		</button>
		
	{/if}
</main>



<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>