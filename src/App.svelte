<script>
	/* import jQuery from 'jquery' */
	export let name
	let your_ip = ""

	let user = { loggedIn: false}


	function toggle() {
		user.loggedIn = !user.loggedIn;
		your_ip = 0
	}

	import { onMount } from "svelte";
    const apiURL = "https://api.ipify.org/?format=json";
	let data = "";
	
	onMount(async function() {
        const response = await fetch(apiURL);
        data = await response.json();
    });

</script>


<main>
	{#if user.loggedIn}
		<h1>Hello, {data.ip}</h1>
		<button on:click={toggle}>
			click for local
		</button>
	{/if}

	{#if !user.loggedIn}
		<h1>Hey 127.0.0.1</h1>
		<button on:click={toggle}>
			click for external
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