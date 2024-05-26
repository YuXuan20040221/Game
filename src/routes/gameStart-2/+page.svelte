<script>
  import Header from "../Header.svelte";

  const text = [
    "你內心的冒險精神如熊熊烈火般，一發不可收拾，",
    "你決定帶上你的得力助手「飛燕」和「小刀」，",
    "共同踏上這趟似乎充滿挑戰的旅程......",
  ];

  function next() {
    window.location.href = "/gameChapterII";
  }
</script>

<svelte:head>
  <title>Game</title>
  <meta name="cover" content="cover of game" />
</svelte:head>
<Header>
  <a href="./" style="color: azure;">
    <i class="fa-solid fa-sliders"></i>
  </a>
  <div style="width: 95%;"></div>
  
  <a href="./" style="color: azure;"><i class="fa-solid fa-house"></i></a>
</Header>

<section>
  <div id="container">
    <div class="typewriter">
      {#each text as t, i}
        <p style="animation-delay: {i * 2}s;">{t}</p>
      {/each}
    </div>
    <button id="nxt_but" on:click={next}>下一關</button>
  </div>
  
</section>

<style>
  #container {
    background-color: rgba(0, 0, 0, 0.6);
    padding: 60px;
    z-index: 1;
  }
  section {
    background-image: url("/src/lib/images/P1-Paper.jpg");
    margin: 0;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
  }

  #nxt_but {
    color: azure;
    background-color: cornflowerblue;
    border-radius: 50px;
    /* width: 80px; */
    padding: 7px 5px;
    font-size: 20px;
    float: right;
    margin: 5px;
    outline: none;
  }

  .typewriter p {
    color: aliceblue;
    height: 25px;
    overflow: hidden;
    font-size: 20px;
    word-break: break-all;
    margin: 10px;
    visibility: hidden;
    animation:
      typing 2s steps(40, end),
      appear 1s forwards;
  }

  /* The typing effect */
  @keyframes typing {
    0% {
      width: 0;
    }
    100% {
      width: 100%;
    }
  }
  @keyframes appear {
    0% {
      visibility: hidden;
    }
    100% {
      visibility: visible;
    }
  }
</style>
