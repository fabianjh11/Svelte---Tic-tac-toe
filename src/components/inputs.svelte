<script>
    let player1 = 'Jugador 1';
    let player2 = 'Jugador 2';
    let pl1 = '';
    let pl2 = '';

    localStorage.setItem('player1', player1);
    localStorage.setItem('player2', player2);

    function save1() {
        pl1!==''? player1 = pl1 : player1 = player1;
        localStorage.setItem('player1', player1);
        console.log(player1);
    }
    function save2() {
        pl2!==''? player2 = pl2 : player2 = player2;
        localStorage.setItem('player2', player2);
        console.log(player2);
    }

</script>

<div class="text">
    <h4>Ingrese los nombres de los jugadores</h4>
</div>
<main>
    <div class="obj">
        <h3>X</h3><input type="text" placeholder="Jugador 1" on:change={() => {save1()}}  bind:value={pl1} maxlength="12">
    </div>
    <div class="obj">
        <h3>O</h3><input type="text" placeholder="Jugador 2" on:change={() => {save2()}} bind:value={pl2} maxlength="12">
    </div>
</main>

<style>
    main
    {
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        border-bottom: 2px solid #000;
    }

    input {
        padding: 10px;
        margin: 0px;
        border: 0px;
        border-bottom: 3px solid rgb(255, 228, 90);
        color: #000;
        border-radius: 1px;
        font-size: 15px;
        font-family: 'Montserrat', sans-serif;
    }
    input:focus {
        background-image: linear-gradient(0deg, rgb(255, 238, 190), rgb(255, 254, 190));
        outline: none;
        color: #3f3f3f;
    }
    input::placeholder {
        color: #999;
        font-family: 'Montserrat', sans-serif;
    }
    input:focus::placeholder {
        color: #777;
    }

    .text {
        border-top: 2px solid #000;
        padding: 5px;
    }
    h4 {
        font-family: 'Montserrat', sans-serif;
        font-size: 20px;
        font-weight: 200;
    }
    .obj {
        display: flex;
        align-items: center;
        justify-content: center;
        margin-left: 10px;
        margin-right: 10px;
    }
    h3 {
        font-size: 30px;
        color: rgb(255, 228, 90);
    }
    .obj * {
        padding: 6px;
        font-family: 'Montserrat', sans-serif;
    }
    
    @media (max-width: 640px) {
		input {
            width: 100px;
            font-size: 12px;
        }
	}
    
</style>