<script>
	import Board from "./components/board.svelte";
	import Header from "./components/header.svelte";
	import Inputs from "./components/inputs.svelte";

	let play = false;

	const handleClick = () => {
		play = !play;
	}

</script>

<Header />
<main>
	{#if !play}
	<Inputs />
	<button on:click={() => {handleClick()}}>JUGAR</button>
	{:else}
	<Board />
	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 400px;
		margin: 0 auto;
	}
	button {
		font-size: 20px;
		font-weight: 100;
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
		padding: 10px;
		margin-top: 50px;
		border-radius: 0px;
		outline: none;
		border: none;
		background-color: #000;
        color: #f7f7f7;
		cursor: pointer;
	}
	button:hover {
		background-color: #393939;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>