<script>
  import Header from "../Header.svelte";
  var input = ["", "", ""];
  let ans_text = ["", "方", "時"];

  let random = Math.floor(Math.random() * 3) + 1;
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

  function ans() {
    let A = true;
    let i = 0;
    for (i = 0; i < 3; i++) {
      if (text[random].ans[i] != input[i]) A = false;
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
