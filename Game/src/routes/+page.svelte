<script>
  import Header from "./Header.svelte";
</script>

<svelte:head>
  <title>Game</title>
  <meta name="cover" content="cover of game" />
</svelte:head>
<Header>
  <span><i class="fa-solid fa-circle-question"></i></span>
</Header>

<section>
  <div id="container">
    <div id="title">盜密傳奇</div>
    <div id="ms_buttons">
      <div id="game_menu">
        <a href="/gameMenu" style="color:cornflowerblue;">遊戲選單</a>
      </div>
      <div id="game_start">
        <a href="/gameEnd" style="color:white;">開始遊戲</a>
      </div>
    </div>
  </div>
</section>

<style>
  section {
    background-image: url("..\lib\images\MainPage2.jpg");
  }

  #title {
    width: auto;
    font-size: 90px;
    color: white;
  }

  #game_menu {
    background-color: white;
    border-radius: 50px;
    padding: 10px;
    font-size: 20px;
  }

  #game_start {
    color: white;
    background-color: cornflowerblue;
    border-radius: 50px;
    padding: 10px;
    font-size: 20px;
  }

  #ms_buttons {
    display: flex;
    justify-content: space-around;
  }
</style>
