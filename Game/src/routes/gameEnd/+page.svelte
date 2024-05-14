<script>
  import Header from "../Header.svelte";
</script>


<Header>
  <span>
    <a href="./" style="color: white;">
      <i class="fa-solid fa-sliders"></i>
    </a>
    <a href="./" style="color: white;">
      <i class="fa-solid fa-house"></i>
    </a>
  </span>
</Header>

<section>
  <video autoplay style="width:100%;" id="video">
    <source src="/src/lib/images/GameEnd.mp4" type="video/mp4" />
    <track
      kind="captions"
      src="captions.vtt"
      srclang="en"
      label="English"
      default
    />
    <!-- 字幕 -->
  </video>
</section>

<style>
  section {
    background-image: url("/src/lib/images/GameEnd.png");
  }
  
</style>
