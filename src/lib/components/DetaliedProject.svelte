<script>
    export let currItem = null
    import {createEventDispatcher} from 'svelte';

    let basesource = "./"

    const dispatch = createEventDispatcher()
    
    function showAll(){
        dispatch("showAll",0)
      }     
</script>
  <head>
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
  </head>
    <div id="selected-item">
      <div id="selected-item-title">
        <button on:click={showAll}><i class="material-icons">arrow_back</i></button>
        <h4>{currItem.name}</h4>
        {#if currItem.link}
          <a href={currItem.link}><img id="github-icon" src={basesource + "logos/github-logo.png"} alt="Github icon">GitHub</a>
        {/if}
      </div>

      <div class="content">
        <p>{currItem.description + currItem.descriptionExtended}</p>
        <div id="img-conteiner">
            {#each currItem.img as x}
              <img src={basesource + x} alt="{currItem.name}">
            {/each}
        </div>
      </div>
    </div>



<style>

  #selected-item{
    height: 100%;
    width: 100%;
    margin: 5px;
    padding: 5px;
    background-color:var(--color4);
    border-radius: 10px;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px 3px 6px;
    display: flex;
    flex-direction: column;
  }

  #selected-item-title{
    font: "Fira Sans", sans-serif;
    height: 60px;
    text-align: center;
    background-color:var(--color4);
    display: grid;
    grid-template-columns: 50px 1fr 50px;
  }

  #selected-item-title button{
    font-weight: bold;
    font-size: large;
    background: none;
    border: none;
    cursor: pointer;
  }
  #selected-item-title button:hover{
    color: var(--color3);
  }

  .content{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 5px;
    background-color: var(--secondary-color);
    flex-grow: 1;
    border-radius: 3px;
  }

  .content p{
    font: 1.2em "Fira Sans", sans-serif;
    margin: 5px;
    padding: 5px;
    line-height: 1.3em;
  }

  #img-conteiner{
    display: block;
    flex-wrap: wrap;
  }

  img{
    margin: 5px;
    border-radius: 5px;
    height: 300px;
  }

  #selected-item-title a{
    align-self: center;
  }

  #github-icon{
    height: 30px;
    width: 30px;
    margin: 0px;
  }
</style>