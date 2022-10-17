<script>
  import DetaliedProject from "./DetaliedProject.svelte";
  let basesource = "./"

  let prevProjectList = [
    {id: 1, 
    name: "Sykkelbris", 
    description:"Sykkelbris er en applikasjon for sykelister i " + 
    "Oslo. Applikasjonen er laget sammen med et team i faget \"IN2000 - Software Engineering med " +
    "prosjektarbeid\".", 
    descriptionExtended: " Sykkelbris inneholder funksjonalitet for å kunne se utvalgte sykkelruter i oslo med en beregning av luftkvalitet for ruten. Applikasjonen har også en modell som viser været inenfor en gitt periode og gir anbefalinger basert på det. Laget for android og hovedsaklig skrevet i kotlin.",
    img:["sykkelbris.png", "sykkelbris_demo.png", "sykkelbris_demo1.png", "sykkelbris_demo2.png", "sykkelbris_demo3.png"],
    },


    {id: 2,
    name: "Gravitasjon animasjon", 
    description:"Pygame basert animasjon for å simulere gravitasjon mellom planeter.", 
    descriptionExtended:"", 
    img:["gravitasjon.JPG"],
    link:"https://github.com/Torkildef/Verdensrommet_sim"},


    {id: 3, 
    name: "Labyrint", 
    description:"Program som bruker tråder og rekusjon for å finne en eller flere veier ut av en labyrint. En utvidet versjon av prosjekt i faget IN1010.",
    descriptionExtended:" Programmet er skrevet i java med hjelp av java awt og swing.", 
    img:["labyrint.JPG"],
    link:"https://github.com/Torkildef/skoleprosjekter/tree/main/traa-labyrint"},


    {id: 4, 
    name: "Parkeringsspill", 
    description:"Et spill hvor man skal parkere en beltevogn. Skrevet i python med bruk av pygame.",
    descriptionExtended:" Parkeringspill startet på under forstegangstjenesten. Et hobbyprosjekt som var basert på min stilling som BV sjåfør. Spillet går ut på å parkere beltevognen innenfor parkeringsplassen.", 
    img:["bv-spill.JPG"],
    link:"https://github.com/Torkildef/BV-parking"},

    {id: 5, 
    name: "Ordspill", 
    description:"Lite ordspill som ligner på hangman der programmet skal finne ut et ord på førrest mulig forsøk.",
    descriptionExtended:" Programmet bruker en ordliste og itererer over den. Basert på input fra brukeren prøver algoritmen å gjette på bokstaven som det er minst sjanse for å gjette feil på.", 
    img:["logos/python-logo.png"],
    link:"https://github.com/Torkildef/ordspill"},

    {id: 5, 
    name: "Medlingstjeneste", 
    description:"Eksamensoppgave i faget IN2140 - Introduksjon til operativsystemer og datakommunikasjon. Programmet er en medlingstjeneste mellom klienter.",
    descriptionExtended:" Består av klienter og en server der klientene bruker en server for å finne en annen klient å kominisere med. ", 
    img:["logos/c-logo.png"],
    link:"https://github.com/Torkildef/skoleprosjekter/tree/main/meldingstjeneste"},
    
  ];

  $: currItem = null
  function showOne(item){
    currItem = item
  }

</script>

<div id="content-conteiner">
  {#if currItem}
  <DetaliedProject currItem = {currItem} on:showAll={()=>currItem = null}></DetaliedProject>
  {:else}
    {#each prevProjectList as item}
        <div on:click={()=>showOne(item)} class="item-conteiner" id={item.id.toString()}>
          <div class="title"><h4>{item.name}</h4></div>
          <div class="content">
            <p>{item.description}</p> 
            <img src={basesource + item.img[0]} alt="{item.name}">
          </div>
        </div>
    {/each}
    <!-- Temporary -->
      <div class="item-conteiner">
        <div class="title"><h4>...</h4></div>
        <div class="content" style="flex-direction:column; align-items:center;">
          <img src={basesource+"working1.gif"} alt="working" style="height:200px; width:auto;">
          <a href="https://github.com/Torkildef"><h3>GitHub</h3></a>
        </div>
      </div>
    {/if}

</div>

<style>
    
  #content-conteiner{
    margin-top: 65px;
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    max-width: 1200px;
    justify-content: center;
  }

  .item-conteiner{
    max-height: 400px;
    overflow-y: auto;
    max-width: 580px;
    width: 100%;
    margin: 5px;
    padding: 5px;
    background-color: var(--color3);
    border-radius: 10px;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px 3px 6px;
    display: flex;
    flex-direction: column;
  }

  .item-conteiner:hover{
    background-color:var(--color4);
    cursor: pointer;
  }


  .title{
    font: "Fira Sans", sans-serif;
    height: 60px;
    text-align: center;
    background-color:var(--color4);
    border-radius: 3px;
  }

  .content{
    display: flex;
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

  img{
    max-width: 50vw;
    max-height: 50vw;
    height: 300px;
    width: 300px;
    margin: 5px;
    border-radius: 5px;
  }
</style>