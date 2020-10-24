<script>
	/* import jQuery from 'jquery' */
	let your_ip = ""

	let user = { loggedIn: false}


	function toggle() {
		user.loggedIn = !user.loggedIn;
		your_ip = 0
	}
	/* https://www.techiediaries.com/consume-json-rest-api-in-svelte-with-fetch-and-onmount/ */
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
		<h1>Hey, 192.168.XXX.XXX</h1>
		<button on:click={toggle}>
			click for external
		</button>
	{/if}
</main>



<style>
	main {
		text-align: center;
		padding: 1em;
		/*max-width: 240px;*/
		margin: 0 auto;
	}
	
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 2em;
		/*font-weight: 450;*/
	}

	button {
		color:  #ff3e00;
		border: solid #ff3e00;;
		background-color: white ;
		/*padding: 8px 16px;*/
		/*width: 30;*/
		border-radius: 1em;
		text-align: center;
	}

	@media (min-width: 20px) {
		main {
			max-width: none;
		}
	}
</style>