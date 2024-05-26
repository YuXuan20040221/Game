<script>
  import Header from "../Header.svelte";
  import Information from "../Information.svelte";
  var answer = ["朱門", "北", "子"];
  var input = ["", "", ""];
  var text = ["地點", "方位", "時間"];
  const info = {
    text: ["密碼學：字驗",
        "說明：中國軍隊第一本真正的軍事通信密碼本《武經總要．字驗》中，紀錄字驗",
        "的用法，在這本書中用一首五言律詩的40個漢字，分别代表40種情況和要求。",
        "假設雙方以唐代王勃的《送杜少府之任蜀川》「城闕輔三秦，風煙望五津。與君",
        "離别意，同是宦游人。海内存知己，天涯若比鄰。無為在歧路，兒女共沾巾」。",
        "作為解碼密鑰。如果軍隊在戰鬥在糧食將盡，需要補充，前方將領就從密碼本中",
        "查出「請糧料」的編碼，假如是第九，而《送杜少府之任蜀川》中的第九字是「五」，",
        "於是請糧將領就將「五」字寫到一件普通公文書碟之中，並在字上加蓋印章。指",
        "揮機關接到這份公文後，查出蓋印章的「五」字，得知「五」字在臨時約好的詩",
        "中列第九，再對照密碼本上的順序，就得知了前方的情報先鋒官得令後默念一遍",
        "詩歌，即可從「戲」中數出命令號碼了。",
        "提示：由題目找到劃記的字是第幾個字，再對應字驗該字在第幾個，",
        "最後可得到對照表對應的第幾行第幾字，即可找出XX地點的X方，X時集合"]
  };

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

  let showInfo = false;
    function toggleInfo(){
        showInfo = true;
    }

    function closeInfo(){
        showInfo = false;
    }
</script>

<Header>
  <a href="/gameMenu" style="color: white;">
    <i class="fa-solid fa-sliders"></i>
  </a>
  <div style="width: 95%;"></div>
  <a
    style="color: white;margin-right: 15px;"
    on:click= {toggleInfo}
  >
    <i class="fa-solid fa-circle-question"></i>
  </a>
  <a href="./" style="color: white;">
    <i class="fa-solid fa-house"></i>
  </a>
</Header>

<section>
  <div id="mask_bg"></div>

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

{#if showInfo}
  <div id="info">
      <Information {...info} close={closeInfo}/>
  </div>
{/if}

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

  #mask_bg {
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
