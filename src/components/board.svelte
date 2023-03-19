<script>
    import { HtmlTag } from "svelte/internal";
    import Square from "./square.svelte";

    let squares = Array(9).fill('');
    let isX = true;
    const pattern = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6]
    ];
    let player1 = localStorage.getItem('player1');
    let player2 = localStorage.getItem('player2');
    let cont = 0;
    let contX = 0;
    let contO = 0;
    let status = 'Turno de ' + (isX? player1 : player2);
    let winner = null;

    const setValue = (idx) => {
        if(squares[idx]!=='' || winner) return;
        isX? squares[idx]='X' : squares[idx]='O';
        squares = [...squares];
        isX = !isX;
        cont += 1;
        console.log(squares);
        state();
    }

    const calcWin = () => {
        for (let i = 0; i < pattern.length; i++) {
            const [cA, cB, cC] = pattern [i];
            if( squares[cA]!== '' && squares[cA] === squares[cB] && squares[cA] === squares[cC]) {
                return squares[cA];
            }
        }
        return null;
    }

    const restart = () => {
        squares = Array(9).fill('');
        cont = 0;
        status = 'Turno de ' + (isX? player1 : player2);
        winner = null;
    }

    const state = () => {
        winner = calcWin();
        if(winner) {
            status = 'Ha ganado ' + (winner==='X'? player1 : player2);
            winner==='X'? contX++ : contO++;
        } else if(cont === 9) {
            status = 'Empate';
        }
        else {
            status = 'Turno de ' + (isX? player1 : player2);
        }
    }
</script>

<div class="wins">
    <h3>Victorias de <em>{player1}</em> : <strong>{contX}</strong></h3>
    <h3>Victorias de <em>{player2}</em> : <strong>{contO}</strong></h3>
</div>
<div class="state">{status}</div>
<div class="board">
    <div class="boardrow">
        <Square value={squares[0]} clicks={() => {setValue(0)}}/>
        <Square value={squares[1]} clicks={() => {setValue(1)}}/>
        <Square value={squares[2]} clicks={() => {setValue(2)}}/>
    </div>
    <div class="boardrow">
        <Square value={squares[3]} clicks={() => {setValue(3)}}/>
        <Square value={squares[4]} clicks={() => {setValue(4)}}/>
        <Square value={squares[5]} clicks={() => {setValue(5)}}/>
    </div>
    <div class="boardrow">
        <Square value={squares[6]} clicks={() => {setValue(6)}}/>
        <Square value={squares[7]} clicks={() => {setValue(7)}}/>
        <Square value={squares[8]} clicks={() => {setValue(8)}}/>
    </div>
</div>
<button class="restart" on:click={() => {restart()}}>Reiniciar</button>

<style>
    .wins {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: row;
        font-family: 'Montserrat', sans-serif;
    }
    .wins h3 {
        padding: 10px;
        margin: 5px;
        box-shadow: rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px 3px 6px;
    }
    strong {
        color: rgb(255, 188, 30);
    }
    .state {
        text-align: center;
        margin: 10px;
        padding: 10px;
        font-size: 30px;
        font-weight: 200;
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
    }
    .board {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
    button {
		font-size: 20px;
		font-weight: 100;
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
		padding: 10px;
		margin-top: 30px;
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

</style>
