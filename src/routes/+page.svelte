<script>
    import Authenticate from "../components/Authenticate.svelte";
    import Statlist from "../components/Statlist.svelte";
    import CharSelect from "../components/CharSelect.svelte";
    import Status from "../components/Status.svelte";
    import Notes from "../components/Notes.svelte";

    
    export let user = 'Anonymous';
    let selectedChar;
    let selectedPanel = 'statList';
    let isAuth = true;

</script>


<div class="mainContainer">
    {#if !isAuth}
    <Authenticate bind:isAuth={isAuth}/>
    {:else}

    
    <div class="char-select">
        <CharSelect id="CharSelect" bind:selectedChar={selectedChar}/>
        <button class="fa fa-save fa_custom"></button>
        <button class="fa fa-sign-out fa_custom" on:click={()=>{isAuth=false}}></button>
    </div>    
    
    <div class="nav-btns">
        <button on:click={()=>{selectedPanel='statList'}}
            class="nav-btn {selectedPanel=='statList' ? 'active' : 'not-active'}">
            stats</button>
        <button on:click={()=>{selectedPanel='status'}}
            class="nav-btn {selectedPanel=='status' ? 'active' : 'not-active'}">
            status</button>
        <button on:click={()=>{selectedPanel='inventory'}}
            class="nav-btn {selectedPanel=='inventory' ? 'active':'not-active'}">
            items & spells</button>
        <button on:click={()=>{selectedPanel='notes'}}
            class="nav-btn {selectedPanel=='notes' ? 'active' : 'not-active'}">
            notes</button>
    </div>

    <div class="panel {selectedPanel=='statList'?'':'hidden'}">
        <Statlist />
    </div>
    <div class="panel {selectedPanel=='status'?'':'hidden'}">
        <Status />
    </div>
    {/if}

    
</div>

<style>
    .mainContainer {
        display: flex;
        flex-direction: column;
        gap:17px;
        margin: 5px auto auto auto;
    }

    .char-select {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        font-weight: 800;
    }

    .fa_custom{
        background-color: transparent;
        border:none;
        border-radius: 90px;
        font-size: 1.9rem;
    }

    .fa_custom:hover{
        background-color: #BABABA;
        color:red;
    }

    .nav-btns{
        position: flex;
        flex-direction: row;
        justify-items: space-between;
    }

    .nav-btn {
        border-radius: 5px;
        font-variant : small-caps;
        font-size: 1.3rem;
        border:none;
        padding:3px;
    }

    .not-active {
        background-color: #d9d9d9;
    }
    .active {
        background-color: #BABABA;
        color:white;
    }

    .hidden {
        display: none;
    }
</style>