<script>
  import ProjectContent from './lib/components/ProjectContent.svelte';
  import AboutMe from './lib/components/AboutMe.svelte';


  let view = "projectView"


</script>

<div id="main">
  <header>
    <div id="header-content">
        <h3>Torkild Finne</h3>
        <div id="header-options">
          <h4 on:click={()=>view = "projectView"}>Mine prosjekter</h4>
          <h4 on:click={()=>view = "aboutMeView"}>Om meg</h4>
        </div>
    </div>
  </header>
  {#if view == "projectView"}
    <ProjectContent/>
  {:else}
    <AboutMe/>
  {/if}

</div>
  
  


<style>

  #main{
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 100%;
    width: 100%;
    background-color: #F5EFE6;
  }

  header{
    position: fixed;
    display:flex;
    justify-content: center; 
    width: 100%;
    min-height: 60px;
    box-shadow: 0 3px 5px -2px rgba(57, 63, 72, 0.3);
    background-color: #AEBDCA;
    }

  #header-content{
    max-width: 1400px;
    width: 100%;
    min-height: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items:center;
  }
  #header-options{
    max-width: 50%;
    display: flex;
    flex-direction: row;


  }
  #header-options h4{
    min-width: 80px;
    height: 50px;
    margin: 3px;
    padding: 2px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  #header-options h4:hover{
    text-decoration: underline;
    cursor: pointer;
  }



</style>
