<script>
  import Header from "../Header.svelte";
  import Information from "../Information.svelte";

  const answer = ["水", "甘", "心", "口", "十", "一", "日", "見"];
  const input = ["", "", "", "", "", "", "", ""];
  const text = [
    "洗塵埃道未甞，",
    "於名利兩相忘。",
    "懷六洞丹霞客，",
    "誦三清紫府章。",
    "裡採蓮歌達旦，",
    "輪明月桂飄香。",
    "高公子還相覓，",
    "得山中好酒漿。",
  ];
  const info = {
    text: ["密碼學：藏頭詩",
      "說明：每一句最後一字含有下一行第一個字"]
  };

  function game() {
    // @ts-ignore
    document.getElementById("Game").style.display = "block";
  }

  function ans() {
    let A = true;
    let i = 0;
    for (i = 0; i < 8; i++) {
      if (answer[i] != input[i]) A = false;
    }
    if (A == false) alert("答案錯誤");
    else {
      window.location.href = "/gameChapterIX-3";
    }
  }
</script>

<svelte:head>
  <title>Game</title>
  <meta name="cover" content="cover of game" />
</svelte:head>
<Header>
  <a href="/gameMenu" style="color: azure;">
    <i class="fa-solid fa-sliders"></i>
  </a>
  <div style="width: 95%;"></div>
  <a
    style="color: white;"
    on:click={() => {
      // @ts-ignore
      document.getElementById("info").style.display = "block";
    }}
  >
    <i class="fa-solid fa-circle-question"></i>
  </a>
    <a href="./" style="color: azure;"><i class="fa-solid fa-house"></i></a>
  </Header
>

<section>
  <button id="lock" class="lock" on:click={game}> 點擊密碼箱 </button>
  <div id="Game">
    {#each text as t, i}
      <p><input type="text" bind:value={input[i]} />{t}</p>
    {/each}
    <button class="lock" style="width: 100px;" on:click={ans}> 開鎖 </button>
  </div>
  <div id="info">
    <Information {...info} />
  </div>
</section>

<style>
  section {
    background-image: url("/src/lib/images/P4-Box2.jpg");
  }

  .lock {
    color: azure;
    background-color: cornflowerblue;
    border-radius: 50px;
    width: 150px;
    padding: 10px;
    font-size: 20px;
    margin: 5px;
  }

  #Game {
    color: azure;
    font-size: 20px;
    width: 60%;
    display: none;
    background-color: rgba(0, 0, 0, 0.7);
    z-index: 1;
    position: absolute;
    text-align: center;
  }
  input {
    background-color: rgba(225, 255, 255, 0.2);
    width: 20px;
    margin: 5px;
    color: azure;
  }

  #info {
    display: none;
  }
</style>
