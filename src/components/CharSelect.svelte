<script>
    export let chars = [
        'goshan',
        'slavec',
        'howhow'
    ];
    export let selectedChar;
    
</script>

<nav>

    <label for="touch"><span>{selectedChar ? selectedChar : 'Characters'}</span></label>               
    <input type="checkbox" id="touch"> 
  
    <ul class="slide">
      <li><p >Create new</p></li>
      {#each chars as char}
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
      <li><p on:click={()=>{selectedChar=char}}>{char}</p></li>
      {/each}
    </ul>
  
</nav> 

<style>
label {
  text-align: center;
}
li p {text-decoration : none; color : #2d2f31;}
li p:hover{background-color: #2d2f31; color : white;}

nav {
  min-width : 220px;
  min-height: 50px;
  background: #d9d9d9;
  border-radius: 5px;
}

span {
  padding : 5px;
  height: 50px;
  background : transparent;
  font-size : 1.7rem;
  font-variant : small-caps;
  cursor : pointer;
  display: block;
  border-radius: 5px;
}

span::after {
  float: right;
  right: 10%;
  content: "+";
}

.slide {
  clear:both;
  width:100%;
  height:0px;
  overflow: hidden;
  text-align: center;
  transition: height .4s ease;
}

.slide li {padding : 15px;}

#touch {position: absolute; opacity: 0; height: 0px;}    

#touch:checked + .slide {height: auto; scroll-behavior: auto;}
</style>