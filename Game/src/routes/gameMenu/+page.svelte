<script>
  import Header from "../Header.svelte";
</script>

<svelte:head>
  <title>Game Menu</title>
  <meta name="description" content="About this app" />
</svelte:head>
<Header>
  <span><a href="./" style="color: white;"><i class="fa-solid fa-house"></i></a></span>
</Header>

<section>
  <div id="container">
    <div id="title_container">
      <div>遊戲選單</div>
    </div>

    <div id="button_container_top">
      <div id="game_all" class="game">
        <div>全關卡</div>
        <div>
          <i class="fa-solid fa-star"></i>
          <i class="fa-solid fa-star"></i>
          <i class="fa-solid fa-star"></i>
        </div>
        <div>尚未遊玩</div>
      </div>

      <a id="game_1" class="game" href="/gameStart">
        <div>關卡 1</div>
        <div>
          <i class="fa-solid fa-star"></i>
          <i class="fa-solid fa-star"></i>
          <i class="fa-solid fa-star"></i>
        </div>
        <div>最佳成績</div>
      </a>

      <a id="game_2" class="game" href="/gameChapterII">
        <div>關卡 2</div>
        <div>
          <i class="fa-regular fa-star"></i>
          <i class="fa-regular fa-star"></i>
          <i class="fa-regular fa-star"></i>
        </div>
        <div>最佳成績</div>
      </a>
    </div>

    <div id="button_container_down">
      <a id="game_3" class="game" href="/gameChapterIII">
        <div>關卡 3</div>
        <div>
          <i class="fa-regular fa-star"></i>
          <i class="fa-regular fa-star"></i>
          <i class="fa-regular fa-star"></i>
        </div>
        <div>尚未遊玩</div>
      </a>

      <a id="game_4" class="game" href="/gameChapterIX">
        <div>關卡 4</div>
        <div>
          <i class="fa-regular fa-star"></i>
          <i class="fa-regular fa-star"></i>
          <i class="fa-regular fa-star"></i>
        </div>
        <div>失敗</div>
      </a>

      <a id="game_5" class="game" href="/gameChapterX">
        <div>關卡 5</div>
        <div>
          <i class="fa-regular fa-star"></i>
          <i class="fa-regular fa-star"></i>
          <i class="fa-regular fa-star"></i>
        </div>
        <div>尚未遊玩</div>
      </a>
    </div>
  </div>
</section>

<style>
  section {
    background-image: url("/src/lib/images/MainPage1.jpg");
  }

  #container {
    background-color: white;
    /* opacity: 0.8; */
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  #title_container {
    display: flex;
    justify-content: center;
    font-size: 30px;
    margin-top: 20px;
  }

  #button_container_top {
    display: flex;
  }

  #button_container_down {
    display: flex;
  }

  .game {
    background-color: rgb(254, 254, 196);
    margin: 30px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 20px;
  }

  .fa-solid.fa-star,
  .fa-regular.fa-star {
    color: gold;
  }
</style>
