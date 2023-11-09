<script>
    import Authenticate from "../components/Authenticate.svelte";
    import Statlist from "../components/Statlist.svelte";
    import CharSelect from "../components/CharSelect.svelte";
    import Status from "../components/Status.svelte";

    
    export let user = 'Anonymous';
    let selectedChar;
    let selectedPanel = 'statList';
    let isAuth = true;

</script>


<div class="mainContainer">
    {#if !isAuth}
    <Authenticate bind:isAuth={isAuth}/>
    {:else}

    <div class="header">
        <p>Hello, <p1>{user}</p1>!</p>
        <button class="fa fa-sign-out fa_custom" on:click={()=>{isAuth=false}}></button>
    </div>
    
    <div class="char-select">
        <CharSelect bind:selectedChar={selectedChar}/>
        <button class="button-62">Save changes</button>
    </div>    
    
    <div class="nav-btns">
        <button on:click={()=>{selectedPanel='statList'}}
            class="nav-btn {selectedPanel=='statList' ? 'active' : 'not-active'}">
            Stats</button>
        <button on:click={()=>{selectedPanel='status'}}
            class="nav-btn {selectedPanel=='status' ? 'active' : 'not-active'}">
            Status</button>
        <button on:click={()=>{selectedPanel='inventory'}}
            class="nav-btn {selectedPanel=='inventory' ? 'active':'not-active'}">
            Items & Spells</button>
        <button on:click={()=>{selectedPanel='notes'}}
            class="nav-btn {selectedPanel=='notes' ? 'active' : 'not-active'}">
            Notes</button>
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
    .header {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        font-size: 1.7rem;
        font-weight: 800;
    }

    .header p1 {
    text-transform: uppercase;
    background-image: linear-gradient(
        -225deg,
        #2c244a 0%,
        #443653 29%,
        #dc8fa9 67%,
        #e7e4a2 100%
    );
    background-size: auto auto;
    background-clip: border-box;
    background-size: 200% auto;
    color: #fff;
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: textclip 2s linear infinite;
    display: inline-block;
    }

    @keyframes textclip {
    to {
        background-position: 200% center;
    }
    }

    .char-select {
        display:flex;
        flex-direction: row;
        justify-content: space-between;
    }

    .fa_custom{
        background-color: transparent;
        border:none;
        border-radius: 90px;
    }

    .fa_custom:hover{
        background-color: #BABABA;
        color:red;
    }
    
    .button-62 {
    height: 50px;
    background: linear-gradient(to bottom right, #ac3f53, #a16947);
    border: 0;
    border-radius: 12px;
    color: #FFFFFF;
    cursor: pointer;
    display: inline-block;
    font-size: 16px;
    font-weight: 500;
    line-height: 2.5;
    outline: transparent;
    padding: 0 1rem;
    text-align: center;
    text-decoration: none;
    transition: box-shadow .2s ease-in-out;
    user-select: none;
    -webkit-user-select: none;
    touch-action: manipulation;
    white-space: nowrap;
    }

    .button-62:not([disabled]):focus {
    box-shadow: 0 0 .25rem rgba(0, 0, 0, 0.5), -.125rem -.125rem 1rem rgba(239, 71, 101, 0.5), .125rem .125rem 1rem rgba(255, 154, 90, 0.5);
    }

    .button-62:not([disabled]):hover {
    box-shadow: 0 0 .25rem rgba(0, 0, 0, 0.5), -.125rem -.125rem 1rem rgba(239, 71, 101, 0.5), .125rem .125rem 1rem rgba(255, 154, 90, 0.5);
    }

    .nav-btns{
        position: flex;
        flex-direction: row;
        justify-items: space-between;
    }

    .nav-btn {
        border-radius: 5px;
        font-variant : small-caps;
        font-size: 1.27rem;
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