<script>
  import {onMount} from 'svelte';
  import {contents} from "./InfoContent.json";
  import Fa from 'svelte-fa';
  import { faEllipsis } from '@fortawesome/free-solid-svg-icons';
  import { faCircle } from '@fortawesome/free-regular-svg-icons';
  let bodyHeight;
  let scrollY;
  let sections = "";
  let sideNav = "";
  let selectBotton = "";

  onMount(() => {
    sections = document.querySelectorAll("#panel")
    sideNav = document.querySelectorAll("#sideNavList")
    selectBotton = document.querySelectorAll("#selectBotton")
    sideNav[0].classList.add("is_active")
    bodyHeight = bodyHeight.scrollHeight;
    document.querySelector("#panelWrapper").style.height = bodyHeight*panel.length+"px"
  })


  
  const handelScroll = () => {

    const sideNavEvent = (index) => {
      if(!sideNav[index+1].classList.contains("is_active")) {
        for(let i = 0; i < sideNav.length; i++) {
        sideNav[i].classList.remove("is_active")
        selectBotton[i].classList.remove("is_active")
        }
        sideNav[index+1].classList.add("is_active")
        selectBotton[index+1].classList.add("is_active")
      }
    }

    const scroll = (index, ifNull) => {
      if (ifNull == "unset") {
        if(bodyHeight*index < scrollY){
          sections[index+1].style.left = `${100-Math.floor((scrollY-bodyHeight*index)/bodyHeight*100)}%`;
          if(scrollY > bodyHeight*(index+1)-100) {
            sections[index+1].style.left = "0%"
          }
          sideNavEvent(index)
        }
      } else {
        if(bodyHeight*index < scrollY && scrollY <= bodyHeight*(index+1) ){
          sections[index+2].style.left = "-100%"
          sections[index+1].style.left = `${100-Math.floor((scrollY-bodyHeight*index)/bodyHeight*100)}%`
          sideNavEvent(index)
        }
        if(scrollY >= bodyHeight*(index+1) ) {
          sections[index+1].style.left = "0%"
        }
      }
      if(scrollY == 0){
        for(let i = 0; i < sideNav.length; i++) {
          sideNav[i].classList.remove("is_active")
          selectBotton[i].classList.remove("is_active")
        }
        sideNav[0].classList.add("is_active")
        selectBotton[0].classList.add("is_active")
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
    handelScroll();
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
    left: 5%;
    top: 50%;
    transform: translate(0%, -50%);
    z-index: 100;
    cursor: pointer;
    padding: 15px 30px;
    background-color: #666;
    border-radius: 5px;
  }

  .side-nav-list {
    color: #b3b3b3;
    transition: all 0.5s;
    display: flex;
    justify-content: start;
    align-items: center;
    white-space: nowrap;
  }

  .side-nav-list .select-botton {
    font-size: 10px;
    margin-right: 8px;
    width: 10px;
    height: 10px;
    line-height: 10px;
    border-radius: 100%;
    text-align: center;
  }

  .side-nav-list:hover,
  .side-nav-list.is_active {
    color: #fff;
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
    top: 20%;
    max-width: 500px;
    margin: 0 auto;
    text-align: center;
    padding: 20px;
  }

  .select-botton.is_active, 
  .side-nav-list:hover .select-botton {
    background-color: #fff;
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

	@media (max-width: 1024px) {
    .side-navigation {
      left: 50%;
      top: 12%;
      transform: translate(-50%, -50%);
      padding: 15px;
      max-width: 1000px;
    }
    .side-navigation ul {
      display: flex;
      align-items: center;
    }
    .side-nav-list {
      justify-content: center;
      margin: 0px 10px;
    }
    .more-icon,
    .select-botton {
      display: none;
    }
	}
	@media (max-width: 680px) {
    .side-navigation {
      font-size: 14px;
      padding: 10px;
    }
    .side-navigation ul {
      display: flex;
      align-items: center;
      justify-content: space-evenly;
    }
    .side-nav-list  {
      width: auto;
      justify-content: start;
    }
	}
	@media (max-width: 560px) {
    .side-navigation {
      width: 440px;
      font-size: 14px;
      padding: 10px;
    }
    .side-navigation ul {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-evenly;
    }
    .side-nav-list {
      width: auto;
      justify-content: start;
      margin: 5px;
    }
	}
	@media (max-width: 480px) {
    .side-navigation {
      width: 330px;
    }
	}

</style>
<nav id="side-navigation" class="side-navigation">
    <div class="more-icon"><Fa icon={faEllipsis} /></div>
    <ul >
      {#each contents as content}
        <li 
          id="sideNavList" 
          class="side-nav-list" 
          on:click={()=>{
            window.scrollTo(0, bodyHeight*content.index)
          }}
        >
          <div id="selectBotton" class="select-botton">
            <Fa icon={faCircle} />
          </div>
          {content.title}
        </li>
      {/each}
    </ul>
</nav>
  
<div 
  id="panelWrapper" 
  class="panel-wrapper" 
  bind:this="{bodyHeight}"
>
  {#each contents as content}
  <section id="panel" class="panel">
    <article class="article background{content.index}">
      <div>
        <h1>{content.title}</h1>
        <p>{@html content.contents}</p>
      </div>
    </article>
  </section>
  {/each}
</div>  

