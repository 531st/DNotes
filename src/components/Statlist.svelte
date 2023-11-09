<script>
    export let statList = [
        {str: 10},
        {con: 10},
        {dex: 10},
        {int: 10},
        {wit: 10},
        {cha: 10},
    ] 
    export let modList = [0, 0, 0, 0, 0, 0]
</script>

<div class="stat-container">
    <table class="stat-panel">
        {#each statList as stat}
            <tr>
                <td id="stat-key">{Object.keys(stat)}</td>
                <td><button class="stat-btn" on:click={()=>{stat[Object.keys(stat)] -= 1}}>-</button></td>
                <td>{stat[Object.keys(stat)]}</td>
                <td><button class="stat-btn" on:click={()=>{stat[Object.keys(stat)] += 1}}>+</button></td>
            </tr>
        {/each}
    </table>
    
    <table class="mod-panel">
        {#each modList as mod}
            <tr>
                <td><button class="stat-btn" on:click={()=>{mod -= 1}}>-</button></td>
                <td>{mod}</td>
                <td><button class="stat-btn" on:click={()=>{mod += 1}}>+</button></td>
            </tr>
        {/each}
    </table>
</div>


<style>
    .stat-container {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        gap: 15px;
    }
    .stat-panel {
        background-color: rgba(205, 159, 159, 0.628);
        box-shadow: 0 0 10px #525252;
        border-radius: 5px;
        font-size: 1.5rem;
        padding: 10px;
        border-spacing: 10px;  
    }

    .mod-panel {
        background-color: rgb(197, 159, 205);
        box-shadow: 0 0 10px #525252;
        border-radius: 5px;
        font-size: 1.5rem;
        padding: 10px;
        border-spacing: 10px;  
    }

    #stat-key{
        font-weight: 700;
    }

    .stat-btn {
        font-size: 1.5rem;
        height: 30px;
        width: 35px;
        border-radius: 30px;
        border: none;
    }

    .stat-btn:hover {
        background-color: #BABABA;
        color:white;
        border-width: 10px;
    }
</style>


