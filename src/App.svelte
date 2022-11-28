<script lang="ts">
  let menu: HTMLDivElement;
  let content: HTMLDivElement;
  let index = 0;
  let slides: {src: string, title: string, description: string, cnop: [string, string, string, string], source?: string}[] = [{
    src: "/mtlu.jpg",
    title: "Mount Lu",
    description: "A drawing of Mount Lu by Shen Zhou (沈周). It was drawn in 1467 and is currently located in the National Palace Museum in Taipei.",
    cnop: ["An ink drawing of Mount Lu", "Recreational Art", "Ming Dynasty, Shen Zhou", "To record what Mount Lu looked like"],
  }, {
    src: "/mathbook.png",
    title: "Suanfa tongzong",
    description: "(Trad. 算法統宗/Simp. 算法统宗) This book is an ancient book about math. The books name literally means \"Compendium of Calculating Methods\". The book contains 595 problems divided into 17 chapters, which can act as an encyclopedia for math at the time.",
    cnop: ["An ancient book about math", "Textbook, Summary of some math problems", "Created is 1592 by Cheng Dawei (程大位)", "To educate and spread math knowledge"],
    source: "/MATHCHINESE.pdf"
  }, {
    src: "/xiyouji.jpg",
    title: "Journey to the West",
    description: "(Trad. 西遊記/Simp. 西游记) This is one of the four classic chinese novels, about the Tang monk and SUN WUKONG's journey to the western paradise (India) to get ancient scriptures from the Buddha.",
    cnop: ["A classic novel about Buddhism and Taoism", "A fiction novel", "Ming Dynasty, Wu Cheng'en, 1592", "To entertain readers (many people still read it today)"],
  }, {
    src: "/britannica.png",
    title: "Britannica (Secondary)",
    description: "Britannica's analysis of the Ming Dynasty's literature.",
    cnop: ["An analysis of Ming Dynasty Literature", "Analysis on the internet", "Britannica, Unknown date", "To educate"],
    source: "https://www.britannica.com/art/Chinese-literature/Ming-dynasty-1368-1644"
  }, {
    src: "/fisher.jpg",
    title: "A Fisher in Autumn",
    description: "A painting of in autumn. The piece is very calm and is comprised of two people on boats, one playing the flute and one lying down on the boat.",
    cnop: ["A painting of some fishers in autumn", "Painting", "Tang Yin, 1523", "To record a sight"]
  }]
  let curname: string = slides[index].title;
  let curdesc: string = slides[index].description;
  
  function slideRight() {
    menu.classList.add("slide-right");
  }

  function navleft() {
    index--;
    if (index < 0) index = slides.length-1;
    curname = slides[index].title;
    curdesc = slides[index].description
  }
  function navright() {
    index++;
    if (index > slides.length-1) index = 0;
    curname = slides[index].title;
    curdesc = slides[index].description
  }

  function showConclusion() {
    content.classList.add("dissappear-please-thank-you-ok-why-are-you-looking-at-this-random-long-ass-class-name")
  }
</script>

<main>
  <div bind:this={menu} class="menu">
    <h1>Ming Dynasty</h1>
    <h2>An exhibition on the Ming Dynasty's Famous Art & Literature</h2>
    <button on:click={slideRight}>
      <h3>Go >>></h3>
    </button>
  </div>
  <div class="browser" bind:this={content}>
    <div class="content">
      <div class="img">
        <img src={slides[index].src} alt={slides[index].title}>
      </div>
      <div class="infobox">
        <h1 class="info-title">{curname}</h1><hr>
        <span class="info-desc">{curdesc}</span>
        <br><br>
        <details>
          <summary>Show CNOP</summary>
          <span class="cnop-content"><span class="cnop-title">Content: </span>{slides[index].cnop[0]}</span><br>
          <span class="cnop-content"><span class="cnop-title">Nature: </span>{slides[index].cnop[1]}</span><br>
          <span class="cnop-content"><span class="cnop-title">Origin: </span>{slides[index].cnop[2]}</span><br>
          <span class="cnop-content"><span class="cnop-title">Purpose: </span>{slides[index].cnop[3]}</span><br>
        </details>
      </div>
      <span class="nav">
        {#if index === slides.length-1}
          <button on:click={showConclusion}>Conclusion</button>
        {/if}
        <button>
          <a href={slides[index]?.source ?? slides[index].src} class="nodec" target="_blank" rel="noreferrer">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-box-arrow-down" viewBox="0 0 16 16">
                <path fill-rule="evenodd" d="M3.5 10a.5.5 0 0 1-.5-.5v-8a.5.5 0 0 1 .5-.5h9a.5.5 0 0 1 .5.5v8a.5.5 0 0 1-.5.5h-2a.5.5 0 0 0 0 1h2A1.5 1.5 0 0 0 14 9.5v-8A1.5 1.5 0 0 0 12.5 0h-9A1.5 1.5 0 0 0 2 1.5v8A1.5 1.5 0 0 0 3.5 11h2a.5.5 0 0 0 0-1h-2z"/>
                <path fill-rule="evenodd" d="M7.646 15.854a.5.5 0 0 0 .708 0l3-3a.5.5 0 0 0-.708-.708L8.5 14.293V5.5a.5.5 0 0 0-1 0v8.793l-2.146-2.147a.5.5 0 0 0-.708.708l3 3z"/>
              </svg>
          </a>
        </button>
        
        <button on:click={navleft}>&lt;</button>
        <button>{index+1}/{slides.length}</button>
        <button on:click={navright}>&gt;</button>
      </span>
      
    </div>
    
  </div>
  <div class="conclusion">
    <h1>Conclusion</h1>
    <span style="width: 50vw; font-size: 1.2rem; z-index: -3;">In conclusion the effects of printing and literature  

      in the Ming dynasty was significant due to the  
      
            development in colored printing technology and  
      
            widespread distribution of books to common people.  
      
            This lead to a rise in average intelligence across the entire country and helps reduce the illiteracy levels of the country. 
      
      Widespread ownership of fiction works introduced a new way to burn free time and increased the vividness of an average person's imagination. </span>
  </div>
</main>