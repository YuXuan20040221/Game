<script>
  import Header from "../Header.svelte";
  var answer = ["朱門", "北", "子"];
  var input = ["", "", ""];
  var text = ["地點", "方位", "時間"];

  function ans() {
    let A = true;
    let i = 0;
    for (i = 0; i < 3; i++) {
      if (answer[i] != input[i]) A = false;
    }
    if (A == false) alert("答案錯誤");
    else {
      window.location.href = "/gameChapterX-3";
    }
  }
</script>

<Header>
  <a href="/gameMenu" style="color: white;">
    <i class="fa-solid fa-sliders"></i>
  </a>
  <div style="width: 95%;"></div>
  <a href="./" style="color: white;">
    <i class="fa-solid fa-house"></i>
  </a>
</Header>

<section>
  <div id="mask"></div>

  <div class="container">
    <div class="bg_mail">
      <div class="question">
        題目：<br />夜長(2)，<br />風(1)蕭蕭，<br />枝頭昏鴉，<br
        />數數(1、2)啼。
      </div>
    </div>

    <div class="bg_mail">
      <div class="question">
        字驗：<br />行盡江南數(5)十程，<br />曉風(9)殘月入華清。<br
        />朝元閣上西風急，<br />都入長(24)楊作雨聲。
      </div>
    </div>

    <div class="bg_mail">
      <div class="question">
        對照表：<br />
        暖客貂鼠裘，悲管逐清瑟。<br />
        勸客駝蹄羹，霜橙壓香桔。<br />
        朱門酒肉臭，路有凍死骨。<br />
        榮枯咫尺異，惆悵難再述。<br />
        北轅就涇渭，官渡又改轍。<br />
        群水從西下，極目高突兀。<br />
        疑是崆峒來，恐觸天柱折。<br />
        河梁幸未坼，枝撐聲悉索。<br />
        行旅相攀援，川廣不可越。<br />
        老妻既異縣，十口隔風雪。<br />
        誰能久不顧？庶往共饑渴。<br />
        入門聞號啕，幼子飢已卒！
      </div>
    </div>
  </div>

  <div id="ans_block">
    {#each text as t, i}
      <p>{t}: <input type="text" bind:value={input[i]} /></p>
    {/each}
    <button class="lock" on:click={ans}> 驗證 </button>
  </div>
</section>

<style>
  section {
    background-image: url("/src/lib/images/P5-House.jpg");
    margin: 0;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    display: flex;
  }

  #mask {
    background-color: rgba(0, 0, 0, 0.6);
    position: absolute;
    left: 0;
    top: 0;
    width: 100vw;
    height: 100vh;
    z-index: 0;
  }

  .bg_mail {
    background-image: url("/src/lib/images/P5-Mail.png");
    background-repeat: no-repeat;
    width: 400px;
    height: 500px;
    background-size: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 10px;
  }

  .question {
    font-size: 20px;
    font-weight: bold;
  }

  #ans_block {
    z-index: 2;
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .container {
    z-index: 2;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
