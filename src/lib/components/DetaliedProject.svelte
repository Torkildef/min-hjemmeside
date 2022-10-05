<script>
    export let currItem = null
    import {createEventDispatcher} from 'svelte';


    const dispatch = createEventDispatcher()
    
    function showAll(){
        dispatch("showAll",0)
      }     
</script>

    <div id="selected-item">
      <div id="selected-item-title">
        <button on:click={showAll}>X</button>
        <div></div>
        <h4>{currItem.name}</h4>
        <div></div>
      </div>

      <div class="content">
        <p>{currItem.description + currItem.descriptionExtended}</p>

    <div id="img-conteiner">
        {#each currItem.img as x}
            <img src={x} alt="{currItem.name}">
        {/each}
    </div>
    {#if currItem.link}
    <a href={currItem.link}>GitHub link</a>
    {/if}
    </div>
    </div>



<style>

  #selected-item{
    height: 100%;
    width: 100%;
    margin: 5px;
    padding: 5px;
    background-color:#7895B2;
    border-radius: 10px;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px 3px 6px;
    display: flex;
    flex-direction: column;
  }

  #selected-item-title{
    font: "Fira Sans", sans-serif;
    height: 60px;
    text-align: center;
    background-color:#7895B2;
    display: grid;
    grid-template-columns: 1fr 5fr 10fr 6fr;
  }

  #selected-item-title button{
    font-weight: bold;
    font-size: large;
    background: none;
    border: none;
    cursor: pointer;
  }
  #selected-item-title button:hover{
    color: #AEBDCA;
  }

  .content{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 5px;
    background-color: #E8DFCA;
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
</style>