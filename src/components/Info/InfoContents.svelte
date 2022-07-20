<script>
  import {onMount} from 'svelte';
  import {infoContents} from "./infoContents.json";

  let bodyHeight;
  let scrollY;
  let sections = "";

  onMount(() => {
    sections = document.querySelectorAll("#panel")
    bodyHeight = bodyHeight.scrollHeight;
    document.querySelector("#panelWrapper").style.height = bodyHeight*panel.length+"px"
  })
  
  const handelScroll = () => {
    const scroll = (index, ifNull) => {
      if (ifNull == "unset") {
        if(bodyHeight*index < scrollY && scrollY <= bodyHeight*(index+1) ){
          sections[index+1].style.left = `${100-Math.floor((scrollY-bodyHeight*index)/bodyHeight*100)}%`
          if(scrollY > bodyHeight*(index+1)-100) {
            sections[index+1].style.left = "0%"
          }
        }
      } else {
        if(bodyHeight*index < scrollY && scrollY <= bodyHeight*(index+1) ){
          sections[index+2].style.left = "-100%"
          sections[index+1].style.left = `${100-Math.floor((scrollY-bodyHeight*index)/bodyHeight*100)}%`
        }
        if(scrollY >= bodyHeight*(index+1) ) {
          sections[index+1].style.left = "0%"
        }
      }
    }
    for(let i = 0; i < sections.length-1; i++) {
      if(i == sections.length-2) {
        scroll(i, "unset")
      } else {
        scroll(i)
      }
    }
  }

  $: {
		scrollY
    handelScroll()
  }
  
</script>

<svelte:window bind:scrollY={scrollY} />
<svelte:body />

<style>
  h1 {
    font-size: 32px;
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

  .article div {
    color: white;
    position: relative;
    display: block;
    top: 40%;
    text-align: center;
  }

  .background0 {
    background: linear-gradient(to left, #243b55, #141E30);
  }
  .background1 {
    background: linear-gradient(to left, #2b4766, #1e2a41);
  }
  .background2 {
    background: linear-gradient(to left, #2f4d70, #1f293f);
  }
  .background3 {
    background: linear-gradient(to left, #34567c, #26334e);
  }
  .background4 {
    background: linear-gradient(to left, #395e88, #2c3a5a);
  }
  .background5 {
    background: linear-gradient(to left, #3f6796, #344469);
  }
</style>
<nav id="side-navigation" class="side-navigation">
    <ul>
      {#each infoContents as infoContent}
        <li on:click={()=>{window.scrollTo(0, bodyHeight*infoContent.index)}}>{infoContent.title}</li>
      {/each}
    </ul>
</nav>
  
<div id="panelWrapper" class="panel-wrapper" bind:this="{bodyHeight}">
  {#each infoContents as infoContent}
  <section id="panel" class="panel">
    <article class="article background{infoContent.index}">
      <div>
        <h1>{infoContent.title}</h1>
        <p>a</p>
      </div>
    </article>
  </section>
  {/each}
</div>  

