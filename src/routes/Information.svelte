<script>
  export let text;

  function leave() {
    document.getElementById("mask").style.display = "none";
    document.getElementById("container_text").style.display = "none";
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

  #mask {
    display: block;
    background-color: rgba(0, 0, 0, 0.6);
    width: 100vw;
    height: 100vh;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 2;
  }

  #container_text {
    display: block;
    background-color: white;
    border-radius: 10px;
    padding: 10px;
    position: absolute;
    z-index: 4;
    top: 300px;
    left: 600px;
  }

  button {
    float: right;
  }
</style>
