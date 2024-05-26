<script>
  import Header from "../Header.svelte";
  import Information from "../Information.svelte";
  var answer = ["朱門", "北", "子"];
  var input = ["", "", ""];
  let ans_text = ["", "方", "時"];

let random = Math.floor(Math.random() * 3);
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

let text = [
  {
    t1: ["夜長(2)，", "風(1)蕭蕭，", "枝頭昏鴉，", "數數(1、2)啼。"],
    t2: [
      "行盡江南數(5)十程，",
      "曉風(9)殘月入華清。",
      "朝元閣上西風急，",
      "都入長(24)楊作雨聲",
    ],
    t3: [
      "暖客貂鼠裘，悲管逐清瑟。",
      "勸客駝蹄羹，霜橙壓香桔。",
      "朱門酒肉臭，路有凍死骨。",
      "榮枯咫尺異，惆悵難再述。",
      "北轅就涇渭，官渡又改轍。",
      "群水從西下，極目高突兀。",
      "疑是崆峒來，恐觸天柱折。",
      "河梁幸未坼，枝撐聲悉索。",
      "行旅相攀援，川廣不可越。",
      "老妻既異縣，十口隔風雪。",
      "誰能久不顧？庶往共饑渴。",
      "入門聞號啕，幼子飢已卒！",
    ],
    ans: ["朱門", "北", "子"],
  },
  {
    t1: ["宵小山(3)賊，", "飛(1)簷走壁行竊，", "人人(1、2)喊打。"],
    t2: [
      "千山(2)鳥飛(4)絕，",
      "萬徑人(8)蹤滅。",
      "孤舟蓑笠翁，",
      "獨釣寒江雪。",
    ],
    t3: [
      "水流花謝兩無情，",
      "送盡東風過楚城。",
      "胡蝶夢中家萬里，",
      "子規枝上月三更。",
      "故園書動經年絕，",
      "華發春唯滿鏡生。",
      "自是不歸歸便得，",
      "五湖煙景有誰爭。",
    ],
    ans: ["五湖", "東", "子"],
  },
  {
    t1: [
      "今夜(2)夜(3)漫長，",
      "正值立秋(4)，",
      " 風微涼，",
      " 願明與君同遊，",
      "仰望漫天雲(5)彩。",
    ],
    t2: [
      "昨夜(2)秋(3)風入漢關，",
      "朔雲(9)邊月滿西山。",
      "更催飛將追驕虜，",
      "莫遣沙場匹馬還。",
    ],
    t3: [
      "舊俗傳荊楚。正江城、梅炎藻夏，做成重午。",
      "門艾釵符關何事，付與痴兒呆女。",
      "耳不聽、湖邊鼉鼓。",
      "獨炷爐香熏衣潤，對瀟瀟、翠竹都忘暑。",
      "時展卷，誦騷語。",
      "新愁不障西山雨。",
      "問樓頭、登臨倦客，有誰懷古。",
      "回首獨醒人何在，空把清尊酹與。",
      "漾不到、瀟湘江渚。",
      "我又相將湖南去，已安排、吊屈嘲漁父。",
      "君有語，但分付。",
    ],
    ans: ["江城", "西", "午"],
  },
];
let WrongAns = 0;

  function ans() {
    let A = true;
    let i = 0;
    for (i = 0; i < 3; i++) {
      if (text[random].ans[i] != input[i]) A = false;
    }
    if (A == false) {
      alert("答案錯誤");
      WrongAns+=1;
      localStorage.setItem("Ch5Wrong", WrongAns.toString());
    } else {
      WrongAns+=1;
      localStorage.setItem("Ch5Wrong", WrongAns.toString());
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
        題目：<br />
        {#each text[random].t1 as t}
          <p>{t}<br /></p>
        {/each}
      </div>
    </div>

    <div class="bg_mail">
      <div class="question">
        字驗：<br />
        {#each text[random].t2 as t}
          <p>{t}<br /></p>
        {/each}
      </div>
    </div>

    <div class="bg_mail">
      <div class="question">
        對照表：<br />
        {#each text[random].t3 as t}
          <p>{t}<br /></p>
        {/each}
      </div>
    </div>
  </div>

  <div id="ans_block">
    {#each ans_text as t, i}
      <p><input type="text" bind:value={input[i]} />{t}</p>
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
    font-size: 15px;
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
