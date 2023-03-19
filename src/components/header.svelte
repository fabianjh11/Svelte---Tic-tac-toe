<script>
</script>

<main>
    <div class="top">
        <h1>Tic Tac Toe</h1>
        <h3>Versión mejorada en Svelte</h3>
    </div>
</main>

<style>
	main {
		display: flex;
		text-align: center;
		align-items: center;
		justify-content: center;
		margin: 0 auto;
		background-color: rgb(255, 228, 90);
	}

	h1 {
		color: #000;
		text-transform: uppercase;
		font-size: 50px;
		font-weight: 100;
	}

	h3 {
		color: #333;
		font-weight: 400;
		padding: 20px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>