<script>
  import {onMount} from 'svelte';

  let bodyHeight;
  let scrollY;

 
const handler = () => {
  bodyHeight = bodyHeight.scrollHeight;
    let sections = document.querySelectorAll("#panel")
    document.querySelector("body").style.height = bodyHeight*panel.length+"px"
      let scrollPercentage = Math.floor(scrollY/bodyHeight*100)

      if(scrollY <= bodyHeight ){
        sections[2].style.left = "-100%"
        sections[1].style.left = `${100-scrollPercentage}%`
      }
      if(scrollY >= bodyHeight) {
        sections[1].style.left = "0%"
      }
      if(bodyHeight < scrollY && scrollY <= bodyHeight*2 ){
        sections[3].style.left = "-100%"
        sections[2].style.left = `${100-Math.floor((scrollY-bodyHeight*1)/bodyHeight*100)}%`
      }
      if(scrollY >= bodyHeight*2 ) {
        sections[2].style.left = "0%"
      }
      if(bodyHeight*2 < scrollY && scrollY <= bodyHeight*3 ){
        sections[4].style.left = "-100%"
        sections[3].style.left = `${100-Math.floor((scrollY-bodyHeight*2)/bodyHeight*100)}%`
      }
      if(scrollY >= bodyHeight*3 ) {
        sections[3].style.left = "0%"
      }
      if(bodyHeight*3 < scrollY && scrollY <= bodyHeight*4 ){
        sections[5].style.left = "-100%"
        sections[4].style.left = `${100-Math.floor((scrollY-bodyHeight*3)/bodyHeight*100)}%`
      }
      if(scrollY >= bodyHeight*4 ) {
        sections[4].style.left = "0%"
      }
      if(bodyHeight*4 < scrollY && scrollY <= bodyHeight*5 ){
        sections[5].style.left = `${100-Math.floor((scrollY-bodyHeight*4)/bodyHeight*100)}%`
      }
}

  onMount(() => {
    
    handler()

  }) 

  $: {
		scrollY
    
    handler()
  }
  
</script>

<svelte:window bind:scrollY={scrollY} />
<svelte:body />

<style>
  h1 {
    font-size: 32px;
    color: white;
    position: relative;
    display: block;
    top: 40%;
    text-align: center;
    text-transform: uppercase;
  }

  .panel-wrapper {
    position: absolute;
    width: 100%;
    height: 100%;
    overflow: hidden;
    top: 0;
    left: 0;
  }

  .side-navigation {
    position: fixed;
    left: 10%;
    top: 50%;
    transform: translate(0%, -50%);
    z-index: 100;
    cursor: pointer;
  }

  .panel {
    position: absolute;
    height: 100%;
    width: 100%;
    left: -100%;
  }
  .panel:first-child {
    left: 0;
  }

  .article {
    position: fixed;
    width: 100%;
    height: 100vh;
  }

  .one {
    background: linear-gradient(to left, #243b55, #141E30);
  }
  .two {
    background-color: #94c356;
  }
  .three {
    background-color: #e3aa59;
  }
  .four {
    background-color: #777;
  }
  .five {
    background-color: #a63ba0;
  }
  .six {
    background-color: #cf5b21;
  }
</style>
<nav id="side-navigation" class="side-navigation">
    <ul>
      <li on:click={()=>{window.scrollTo(0, bodyHeight*0)}}>TITLE A</li>
      <li on:click={()=>{window.scrollTo(0, bodyHeight*1)}}>TITLE B</li>
      <li on:click={()=>{window.scrollTo(0, bodyHeight*2)}}>TITLE C</li>
      <li on:click={()=>{window.scrollTo(0, bodyHeight*3)}}>TITLE D</li>
      <li on:click={()=>{window.scrollTo(0, bodyHeight*4)}}>TITLE E</li>
      <li on:click={()=>{window.scrollTo(0, bodyHeight*5)}}>TITLE F</li>
    </ul>
</nav>
  
<div id="panelWrapper" class="panel-wrapper" bind:this="{bodyHeight}">
    <section id="panel" class="panel one">
      <article class="article">
        <h1>TITLE A</h1>
      </article>
    </section>
    <section id="panel" class="panel two">
      <article class="article">
        <h1>TITLE B</h1>
      </article>
    </section>
    <section id="panel" class="panel three">
      <article class="article">
        <h1>TITLE C</h1>
      </article>
    </section>
    <section id="panel" class="panel four">
      <article class="article">
        <h1>TITLE D</h1>
      </article>
    </section>
    <section id="panel" class="panel five">
      <article class="article">
        <h1>TITLE E</h1>
      </article>
    </section>
    <section id="panel" class="panel six">
      <article class="article">
        <h1>TITLE F</h1>
      </article>
    </section>
</div>  

