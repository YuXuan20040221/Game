<script>
  export let text;
  /**
   * @type {() => void}
   */
   export let close;

  function leave() {
    // @ts-ignore
    document.getElementById("mask").style.display = "none";
    // @ts-ignore
    document.getElementById("container_text").style.display = "none";
    close();
  }
</script>

<section>
  <div id="mask"></div>
  <div id="container_text">
    {#each text as t}
      <div>{t}</div>
    {/each}
    <button on:click={leave}>離開</button>
  </div>
  
</section>

<style>

  section{
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
  }

  #mask {
    display: block;
    background-color: rgba(0, 0, 0, 0.6);
    width: 100vw;
    height: 100vh;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 3;
  }

  #container_text {
    display: block;
    background-color: white;
    border-radius: 10px;
    padding: 10px;
    /* position: absolute; */
    z-index: 4;
    /* top: 300px;
    left: 600px; */
  }

  button {
    float: right;
  }
</style>
