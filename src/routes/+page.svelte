<script>
  import Header from "./Header.svelte";
  import Information from "./Information.svelte";

  let showInfo = false;
  function toggleInfo() {
      showInfo = true;
  }

  function closeInfo() {
      showInfo = false;
  }

  const info = {
        text: [
            "遊戲簡介：「盜密傳奇」是一款以中國古代密碼學為靈感啟發的密室通關遊戲，玩家經由戲劇情，不僅能了解宋朝時期的朝政概況，透過",
            "用中國古代密碼學破解關卡，學習前人的智慧。",
            "遊戲玩法：",
            "1. 每一個關卡都以一個密碼學為主題設計，玩家可透過劇情以及螢幕由上角的「資訊」圖案，獲得該密碼學的介紹，也可作為通關的提示",
            "2. 會記錄關卡答題的次數以計算每關的星等，答題至破解的次數越少，星星數越高",
            "3. 點擊每關的左上角圖標，可跳回至關卡列表；右上角圖標則是回到遊戲起始畫面"
        ],
    };

</script>

<svelte:head>
  <title>Game</title>
  <meta name="cover" content="cover of game" />
</svelte:head>
<Header>
  <a style="color: white;margin-right: 15px;" on:click={toggleInfo}>
    <i class="fa-solid fa-circle-question"></i>
  </a>
</Header>

<section>
  <div id="container">
    <div id="title">盜密傳奇</div>
    <div id="ms_buttons">
      <div id="game_menu">
        <a href="/gameMenu" style="color:cornflowerblue;">遊戲選單</a>
      </div>
      <div id="game_start">
        <a href="/gameStart-0" style="color:white;">開始遊戲</a>
      </div>
    </div>
  </div>
</section>

{#if showInfo}
    <div id="info">
        <Information {...info} close={closeInfo} />
    </div>
{/if}

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
