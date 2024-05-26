<script>
  import Header from "../Header.svelte";
  import Information from "../Information.svelte";

  const input = ["", "", "", "", "", "", "", ""];
  const text = [
        {
            t: [
                "洗塵埃道未甞，",
                "於名利兩相忘。",
                "懷六洞丹霞客，",
                "誦三清紫府章。",
                "裡採蓮歌達旦，",
                "輪明月桂飄香。",
                "高公子還相覓，",
                "得山中好酒漿。",
            ],
            ans: ["水", "甘", "心", "口", "十", "一", "日", "見"],
        },
        {
            t: [
                "上瑤台興倍增，",
                "傳百戰集良朋。",
                "明書幌白如晝，",
                "發征途河已冰。",
                "淺梅寒人共談，",
                "溫爐暖客閒憑。",
                "情擬鬥尖義韻，",
                "闕詩戰肅氣凝。",
            ],
            ans: ["疑", "曾", "月", "旦", "水", "火", "心", "貝"],
        },
    ];
  const info = {
    text: ["密碼學：藏頭詩",
      "說明：明代學者徐師曾在他的《詩體明辯》中說：「藏頭詩，每句頭字皆藏於每句尾字也。」",
      "是說每句的第一字，都隱藏於前句的末一字。這是利用漢字中合體字多的特點，從前句末一字",
      "分離出其中的一个「部件」，作為次句的首字。就是最初的「藏頭拆字詩」或「離合藏頭詩」。",
      "最早的藏頭詩為唐白居易的《游紫霄宫》",
      "   水洗塵埃道未甞，甘於名利兩相忘。",
      "   心懷六洞丹霞客，口誦三清紫府章。",
      "   十里採蓮歌達旦，一輪明月桂飄香。",
      "   日高公子還相覓，見得山中好酒漿。"]
  };

  let WrongAns = 0;
    let random = Math.floor(Math.random() * 2);

  function game() {
    // @ts-ignore
    document.getElementById("Game").style.display = "block";
  }

    function ans() {
        let A = true;
        let i = 0;
        for (i = 0; i < 8; i++) {
            if (text[random].ans[i] != input[i]) A = false;
        }
        if (A == false) {
            alert("答案錯誤");
            WrongAns += 1;
            localStorage.setItem("Ch4Wrong", WrongAns.toString());
        } else {
            WrongAns += 1;
            localStorage.setItem("Ch4Wrong", WrongAns.toString());
            window.location.href = "/gameChapterIX-3";
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

<svelte:head>
  <title>Game</title>
  <meta name="cover" content="cover of game" />
  <title>Game</title>
  <meta name="cover" content="cover of game" />
</svelte:head>
<Header>
  <a href="/gameMenu" style="color: azure;">
    <i class="fa-solid fa-sliders"></i>
  </a>
  <div style="width: 95%;"></div>
  <a
    style="color: white; margin-right: 15px;"
    on:click= {toggleInfo}
  >
    <i class="fa-solid fa-circle-question"></i>
  </a>
    <a href="./" style="color: azure;"><i class="fa-solid fa-house"></i></a>
  </Header
>

<section>
    <button id="lock" class="lock" on:click={game}> 點擊密碼箱 </button>
    <div id="Game">
        {#each text[random].t as t, i}
            <p><input type="text" bind:value={input[i]} />{t}</p>
        {/each}
        <button class="lock" style="width: 100px;" on:click={ans}>
            開鎖
        </button>
    </div>
  
</section>

{#if showInfo}
  <div id="info">
      <Information {...info} close={closeInfo}/>
  </div>
{/if}

<style>
  section {
    background-image: url("/src/lib/images/P4-Box2.jpg");
  }
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
    z-index: 0;
    position: absolute;
    text-align: center;
  }
  input {
    background-color: rgba(225, 255, 255, 0.2);
    width: 20px;
    margin: 5px;
    color: azure;
  }

</style>
