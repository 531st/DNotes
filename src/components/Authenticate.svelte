<script>
    import {createEventDispatcher} from 'svelte'

    let email ='';
    let pass ='';
    let confirmPass ='';
    let error = false;
    let register = false;
    export let isAuth = false;


    function handleAuthenticate(){
        if (!email || !pass || (register && !confirmPass)){
            error = true;
            return
        }
    }

    function handleRegister(){
        register = !register
    }
</script>


<div class="authContainer">
    <form method="POST" action='/'>
        <h1>{register ? 'Register' : 'Login'}</h1>
        {#if error}
            <p class="error">d1, critical failure. You shall not enter!</p>
        {/if}
        <label>
            <p class={email ? 'above' : 'center'}>Email</p>
            <input bind:value={email} type="email" placeholder="Email" />
        </label>
        <label>
            <p class={pass ? 'above' : 'center'}>Password</p>
            <input bind:value={pass} type="password" placeholder="Password" />
        </label>
        {#if register}
        <label>
            <p class={confirmPass ? 'above' : 'center'}>Confirm Password</p>
            <input bind:value={confirmPass} type="password" placeholder="Confirm Password" />
        </label>
        {/if}
        <button type="button" on:click={()=>{isAuth=true}}>Submit</button>
    </form>
    <div class="options">
        <p>Or</p>
        {#if register}
            <div>
                <p>Already have an account?</p>
                <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
                <p on:click={handleRegister} on:keydown={()=>{}}>Login</p>
            </div>
        {:else}
            <div>
                <p>Don't have an account yet?</p>
                <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
                <p on:click={handleRegister} on:keydown={()=>{}}>Register</p>
            </div>
        {/if}
    </div>
</div>


<style>
    .authContainer {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        flex: 1;
        padding: 24px;
        width: 55vh;
    }

    form {
        display: flex;
        flex-direction: column;
        gap: 14px;
    }

    form,
    .options {
        width: 400px;
        max-width: 100%;
        margin: 0 auto;
    }

    form label {
        position: relative;
        border: 1px solid #878787;
        border-radius: 5px;
    }

    form label:hover {
        border: 1px solid darkcyan;
    }

    form input {
        width: 100%;
        border: none;
        background-color: transparent;
        padding: 14px;
    }

    form input:focus {
        border: none;
        outline: none;
    }

    form label:focus-within {
        border-color: cyan;
    }

    form button {
        background: #878787;
        color: black;
        border: none;
        padding: 14px 0;
        border-radius: 5px;
        cursor: pointer;
        font-size: 1.5rem;
    }

    form button:hover {
        background: #525252;
        color: cyan;
    }

    h1 {
        text-align: center;
        font-size: 3rem;
    }

    .above,
    .center {
        position: absolute;
        transform: translateY(-50%);
        pointer-events: none;
        color:black;
        border-radius: 5px;
        padding: 0 6px;
        font-size: 0.8rem;
        font-weight: 600;
    }

    .above {
        top: 0;
        left: 10px;
        background: #878787;
        border: 1px solid #525252;
        font-size: 0.7rem;
    }

    .center {
        top: 50%;
        left: 6px;
        border: 1px solid transparent;
        opacity: 0;
    }

    .error {
        color: rgb(214, 2, 2);
        font-size: 1.3rem;
    }

    .options {
        padding: 14px 0;
        overflow: hidden;
        font-size: 1.1rem;
        gap: 4px;
    }

    .options > p {
        position: relative;
        text-align: center;
        width: fit-content;
        margin: 0 auto;
        padding: 0 8px;
    }

    .options > p::after,
    .options > p::before {
        position: absolute;
        content: "";
        top: 50%;
        transform: translateY(-50%);
        width: 100vw;
        height: 1.5px;
        background: #878787;
    }

    .options > p::after{
        right: 100%;
    }

    .options > p::before{
        left: 100%;
    }

    .options div{
        display: flex;
        align-items: center;
        gap: 8px;
        justify-content: center;
    }

    .options div p:last-of-type {
        color: darkcyan;
        cursor: pointer;
    }

    .options div p:last-of-type:hover {
        color: cyan;
        cursor: pointer;
    }
</style>