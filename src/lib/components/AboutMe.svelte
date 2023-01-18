<script>
  
  
  let logosurce = "./logos/"

  let codeImages = [
    {name: "Python", img: "python-logo.png"},
    {name: "Java", img: "java-logo.png"},
    {name: "Kotlin", img: "kotlin-logo.png"},
    {name: "C", img: "c-logo.png"},
    {name: "JavaScript", img: "javascript-logo.png"},
    {name: "HTML", img: "html-logo.png"},
    {name: "CSS", img: "css-logo.png"},
    {name: "Svelte", img: "svelte.svg"},
    {name: "Scheme", img: "scheme-logo.svg"},
  ]

  let sosials = [
    {name: "LinkedIn", img: "linkedin-logo.png", link: "https://www.linkedin.com/in/torkild-finne-aa1760251/"},
    {name: "GitHub", img: "github-logo.png", link: "https://github.com/Torkildef"},
    {name: "Facebook", img: "facebook-logo.png", link: "https://www.facebook.com/torkild.finne"},
    {name: "Instagram", img: "instagram-logo.png", link: "https://www.instagram.com/torkildfinne/"},
  ]

  let courses = [
    {code:"IN1000", name: "Introduksjon til informatikk", link:"https://www.uio.no/studier/emner/matnat/ifi/IN1000/"},
    {code:"IN1020", name: "Introduksjon til datateknologi", link:"https://www.uio.no/studier/emner/matnat/ifi/IN1020/"},
    {code:"IN1010", name: "Objektorientert programmering", link:"https://www.uio.no/studier/emner/matnat/ifi/IN1010/"},
    {code:"IN1030", name: "Systemer, krav og konsekvenser", link:"https://www.uio.no/studier/emner/matnat/ifi/IN1030/"},
    {code:"IN1150", name: "Logiske metoder", link:"https://www.uio.no/studier/emner/matnat/ifi/IN1150/"},
    {code:"IN2010", name: "Algoritmer og datastrukturer", link:"https://www.uio.no/studier/emner/matnat/ifi/IN2010/"},
    {code:"IN2090", name: "Databaser og datamodellering", link:"https://www.uio.no/studier/emner/matnat/ifi/IN2090/"},
    {code:"IN2120", name: "Informasjonssikkerhet", link:"https://www.uio.no/studier/emner/matnat/ifi/IN2120/"},
    {code:"IN2000", name: "Software Engineering med prosjektarbeid", link:"https://www.uio.no/studier/emner/matnat/ifi/IN2000/"},
    {code:"IN2140", name: "Introduksjon til operativsystemer og datakommunikasjon", link:"https://www.uio.no/studier/emner/matnat/ifi/IN2140/"},
    {code:"IN2040", name: "Funksjonell programmering", link:"https://www.uio.no/studier/emner/matnat/ifi/IN2040/", onGoing: true},
    {code:"IN2030", name: "Prosjektoppgave i programering", link:"https://www.uio.no/studier/emner/matnat/ifi/IN2030/", onGoing: true},
    {code:"IN3110", name: "Problemløsning med høynivå-språk", link:"https://www.uio.no/studier/emner/matnat/ifi/IN3110/", onGoing: true},
]  

  const animationBox = {width: 0, height: 0};
  codeImages.forEach((item) => {
    // random number between 0.5 and 1.5
    item.speedx = Math.random() * 0.5 + 0.5;
    item.speedy = Math.random() * 0.5 + 0.5;
    item.x = Math.random() * 500;
    item.y = Math.random() * 300;
    item.size = 50;

  })

  // animation loop for the codeImages with interval 16ms (60fps)
  setInterval(animation, 16);
  function animation(){
    let box = document.getElementById("logo-animation")
    animationBox.width = box.clientWidth
    animationBox.height = box.clientHeight

    //for each codeImages2
    for(let i = 0; i < codeImages.length; i++){
      let item = codeImages[i]

      let x = item.x + item.speedx
      let y = item.y + item.speedy

      if(x < 0){
        item.speedx = - item.speedx
        item.x = 1;
      }
      else if(x > animationBox.width - item.size){
        item.speedx = -item.speedx
        item.x = animationBox.width - item.size - 1;
      }
      else{
        codeImages[i].x = x
      }
      if(y < 0){
        item.speedy = -item.speedy
        item.y = 0;
      }
      else if(y > animationBox.height - item.size){
        item.speedy = -item.speedy
        item.y = animationBox.height - item.size - 1;
      }
      else{
        codeImages[i].y = y
      }
    }
  }



</script>

<div id="content-conteiner">
  <div class="box-content" style="display: inline-block;" >
    <img id="portrait" src="./selvportrett.jpg" alt="of me">   
    <p>Hei! Mitt navn er Torkild Engen Finne. Jeg er en 23 år gammel utvikler som går 3-året 
      på <a href="https://www.uio.no/studier/program/informatikk-programmering/">Informatikk
      - programmering og systemarkitektur</a> ved universitetet i Oslo. Ved siden av studiene
      er jeg en aktiv person som liker friluft, fart og spenning. Tidligere har jeg også 
      satset alpint på nasjonalt nivå og jobber fortiden som alpintrener i Kjelsås. Jeg har erfaring med IT-utivkling gjennom sommerjobb i DIPS AS. 
      Jeg har også jobbet som postbud, resepsjonist og tilbrakt et år i førstegangstjenesten. 
      Kontakt meg gjerne gjennom <a href="https://www.linkedin.com/in/torkild-finne-aa1760251/">linkedin</a>.
    </p>
  </div>

  
  <div class="box-content">

      <div id="logo-animation"> 
        {#each codeImages as img}
        <img
        title={img.name}
        src={logosurce+img.img}
        alt="code language"
        style="
            max-width: {img.size}px;
            max-height: {img.size}px;
            left:{Math.round(img.x*10)/10}px;
            top:{Math.round(img.y*10)/10}px;">
        {/each}
      </div>

      <table id="code-list">
        <tr><th style="border-bottom:1px solid black;">Teknologier</th></tr>
        <tr><td>Python</td></tr>
        <tr><td>Java</td></tr>
        <tr><td>Kotlin</td></tr>
        <tr><td>Javascript, html, css</td></tr>
        <tr><td>Svelte</td></tr>
        <tr><td>C</td></tr>
        <tr><td>SQL</td></tr>
        <tr><td>Scheme</td></tr>
      </table>
    </div>

    <div class="box-content">
      <table id="courses-table">
        
        <th style="border-bottom:1px solid black;">Emner</th>
        {#each courses as course}
        <tr on:click={()=>window.open(course.link)}>
          <span>
            <td>
              {course.code}
            </td>
            <td>
              - {course.name}
            </td>
          </span>
        </tr>
        {/each}
      </table>
    </div>
    
    <div class="box-content">
      <!-- Hmm -->
    </div>

    <div class="box-content">
      {#each sosials as sosial}
        <a title={sosial.name} href={sosial.link}>
          <img class="sosiale-img" src={logosurce + sosial.img} alt={sosial.name}>
        </a>
      {/each}
    </div>
</div>
  
  
  <style>    
    #content-conteiner{
      margin-top: 65px;
      display: flex;
      flex-direction: column;
      max-width: 1200px;
      justify-content: center;
      align-items: center;
      padding: 10px;
      font-family: "NewZaldBook";
      font-size: 1.5em;

    }
    #content-conteiner p{
      line-height: 1.6;
    }

    .box-content{
      margin-bottom: 20px;
      display: flex;
      flex-direction: row;
      justify-content: space-evenly;
      width: 100%;
      max-width: 800px;
      padding: 10px;
      background-color: var(--secondary-color);
      border-radius: 10px;
      box-shadow: rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px 3px 6px;
    }

    .box-content #portrait{
      float: right;
      width: 100%;
      height: 100%;
      max-width: 200px;
      max-height: 200px;
      border-radius: 10px;
      margin-left: 20px;
    }
    

    

    #code-list{
      min-width: 230px;
      margin-left: 50px;
    }

    #logo-animation{
      position: relative;
      width: 100%;
      }

    #logo-animation img{
      position: absolute;
      z-index: 0;
    }

    #courses-table{
      font-family: Arial, Helvetica, sans-serif;
      border-collapse: collapse;
      width: 100%;
    }

    #courses-table td, #courses-table th {
      padding: 8px;
    }
    
    #courses-table tr:nth-child(even){background-color: var(--color3);}
    
    #courses-table tr:hover{
      background-color: var(--color4);
      cursor: pointer;
    }
    .sosiale-img{
      width: 100%;
      height: 100%;
      max-width: 50px;
      max-height: 50px;
      margin: 10px;
    }


    </style>