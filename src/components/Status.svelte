<script>
    export let currentHp = 22;
    export let maxHp=27;
    export let tempHp = 4;
</script>

<div class="status-container">
    <div class="hp-spell-col">
        <div class="hp-panel">
            <div class="hp-row">
                <p style="color:#FF4600;">&#10084;</p>
                <input class="hp-input" bind:value={currentHp}>
                <p style="color:white; font-size:20px;">/</p>
                <input class="hp-input" bind:value={maxHp}>
            </div>
            <div class="hp-row">
                <p style="color:white;">&#10084;</p>
                <input class="hp-input" bind:value={tempHp}>
            </div>
        </div>
        <div class="spell-panel">
            <p>Spell Slots</p>
        </div>
    </div>
</div>

<style>
    .status-container{
        font-variant : small-caps;
        min-width: 36vh;
    }

    .hp-spell-col {
        display: flex;
        flex-direction: column;
        gap: 7px;
    }

    .hp-panel{
        display: flex;
        flex-direction: column;
        width: 150px;
        background-color: rgb(110, 138, 98);
        border-radius: 5px;
        gap: 5px;
        padding: 3px;
        font-size: 1.2rem;
        color: white;
        
    }

    .hp-row{
        display: flex;
        flex-direction: row;
        padding:2px;
        gap: 3px;
    }

    .hp-input{
        width:3.2rem;
        border-radius: 5px;
        border: none;
        background-color: #d9d9d9;
        padding:2px;
        text-align: center;
        font-size: 20px;
    }

    .spell-panel {
        
        display: flex;
        flex-direction: column;
        width: 150px;
        background-color: rgb(136, 133, 189);
        border-radius: 5px;
        gap: 5px;
        padding: 3px;
        font-size: 1.2rem;
        color: white;
        text-align: center;
    }
</style>