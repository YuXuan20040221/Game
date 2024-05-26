<script>
  import Header from "../Header.svelte";
</script>


<Header>
  <a href="/gameMenu" style="color: azure;">
      <i class="fa-solid fa-sliders"></i>
  </a>
  <div style="width: 95%;"></div>
  <a href="./" style="color: azure;"><i class="fa-solid fa-house"></i></a>
</Header>

<section>
  <video autoplay style="width:95%;" id="video">
    <source src="/src/lib/images/GameStart.mp4" type="video/mp4" />
    <track
      kind="captions"
      src="captions.vtt"
      srclang="en"
      label="English"
      default
    />
    <!-- 字幕 -->
  </video>
  <div class="game_start">
    <a href="/gameStart" style="color:white;">第一關</a>
  </div>
</section>

<style>
  section {
    background-image: url("/src/lib/images/Start.jpg");
  }

  .game_start {
    top: 5%;
    left: 80%;
    z-index: 1;
    color: white;
    background-color: cornflowerblue;
    border-radius: 50px;
    padding: 10px;
    font-size: 20px;
    position: absolute;
  }
  
</style>
