<script>
    export let currentHp = 22;
    export let maxHp=27;
    export let tempHp = 4;
    export let spellSlots = [
        {lvl: 1, currentVal: 1, maxVal: 4},
        {lvl: 2, currentVal: 2, maxVal: 3},
        {lvl: 3, currentVal: 2, maxVal: 2},
    ];
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
            <p>ПЕРЕДЕЛОЙ</p>
                {#each spellSlots as slot}
                    <div class="spell-row">
                        
                    </div>
                {/each}
                <div>
                    <button class="spell-btn">-</button>
                    <button class="spell-btn">+</button>
                </div>
        </div>
    </div>
    <div class="notes-panel">
        here
    </div>
</div>

<style>
    .status-container{
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        gap: 15px;
    }   

    .hp-spell-col {
        display: flex;
        flex-direction: column;
        gap: 15px;
    }

    .hp-panel{
        display: flex;
        flex-direction: column;
        width: 162px;
        background-color: rgb(110, 138, 98);
        box-shadow: 0 0 10px #525252;
        border-radius: 5px;
        font-size: 1.5rem;
        font-variant : small-caps;
        padding: 5px;
        
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
        width: 162px;
        background-color: rgb(136, 133, 189);
        box-shadow: 0 0 10px #525252;
        border-radius: 5px;
        font-size: 1.5rem;
        color: white;
        font-variant : small-caps;
        padding: 5px;
        align-items: center;
        justify-items: space-between;
    }

    .spell-row{
        display: flex;
        flex-direction: row;
        justify-content:space-between;
    }

    .spell-input {
        width: 30px;
        height:34px;
        border-radius: 5px;
        border: none;
        background-color: #d9d9d9;
        padding:2px;
        text-align: center;
        font-size: 20px;
    }

    .spell-btn {
        border-radius: 50%;
        height: 23px;
        width:23px;
        font-size: 20px;
        border: none;
        background-color: #d9d9d9;
    }

    .notes-panel {
        display: flex;
        flex-direction: column;
        width: 180px;
        background-color: rgb(172, 127, 71);
        box-shadow: 0 0 10px #525252;
        border-radius: 5px;
        font-size: 1.5rem;
        font-variant : small-caps;
        padding: 5px;
        color: white;
    }
</style>