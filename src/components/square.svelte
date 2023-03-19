<script>
    export let value = '';
    export let clicks;
</script>

<button on:click={clicks}>{value}</button>

<style>
    button {
        width: 80px;
        height: 80px;
        text-align: center;
        font-size: 35px;
        font-family: 'Montserrat', sans-serif;
        float: left;
        background-color: #000;
        color: #f7f7f7;
        font-weight: 200;
        border: none;
        margin: 2px;
        cursor: pointer;
    }
</style>