<script>
    import Header from "../Header.svelte";
    import Information from "../Information.svelte";

    const text = [
        "某日，你收到了一封密信，隱藏在背後的那",
        "個人為了考驗你的真實實力，在信中用了一",
        "個特別的加密方式，似乎是在指引了一個神",
        "秘寶藏的埋藏地點......",
    ];

    let random = Math.floor(Math.random() * 4) + 1;
    const mail_text = [
        {
            t: ["樺樹林裡無木，", "木在田中，", "閒人窗紗掩月，", "取刀一剪。"],
            ans: "華東門前",
        },
        { t: ["冬月江畔鳥翩躚，", "士兵途經寸難移。"], ans: "青鴻寺" },
        {
            t: [
                "雨後山水昏如睡，",
                "明日鬱結盼出走，",
                "門中俠客帽欲摘，",
                "放眼天地任遨遊。",
            ],
            ans: "雪月閣",
        },
        {
            t: ["牛角上綁刀，", "離人心上秋燈閃閃人兒不見，", "悶昏昏笑話無心"],
            ans: "解愁門",
        },
    ];
    const info = {
        text: [
            "密碼學：析字法",
            "說明：古人將漢字的構造方法分析、歸納為「六書」，即象形、指事、會意、形聲、轉注、假借。依此將漢字分為音、形、義三個方面。",
            "漢語傳統修辭學根據這一原理，創造了「析字格」這種遊戲式的隱語。如《後漢書·五行志》：「千里草，何青青；十日卜，不得生。」范",
            "曄云：「千里草為董，十日卜為卓」。",
            "後在軍事活動中也得以運用。公元683年(唐弘道元年)，唐高宗死后唐中宗即位。武則天以皇太后名義臨朝稱帝，不到兩個月又廢唐中宗，",
            "立第四子李旦(唐睿宗)為皇帝，但朝政大事均由自己專斷。因此引起大臣裴炎、徐敬業和駱賓王等人的强烈反對。於是，徐敬業聚兵10萬",
            "人，於揚州起兵，反抗武則天統治。裴炎為徐敬業作内應，欲以析字手段为為其傳遞秘密訊息。後因有人告密，裴炎被捕，其未發出的密",
            "信落到武則天手中。這封密信上只有「青鵝」二字，裙臣對此大惑不解。最後還是武則天破解了「青鵝」的秘密：「青」字拆開來就是",
            "「十二月」；而「鵝」字拆開來就是「我自與」。密信的意思是讓徐敬業、駱賓王等率兵於12月進發，裴炎在内部接應。「青鵝」破譯後，",
            "裴炎遂被殺，接着，武則天派兵擊敗了徐敬業和駱賓王的武裝反抗。",
        ],
    };


    var input = "";
    let WrongAns = 0;

    function openMail() {
        // @ts-ignore
        document.getElementById("mail").style.display = "block";
        // @ts-ignore
        document.getElementById("mask").style.display = "block";
    }

    function commit() {
        if (input != mail_text[random].ans) {
            alert("答案錯誤!");
            WrongAns += 1;
            localStorage.setItem("Ch1Wrong", WrongAns.toString());
        } else {
            WrongAns += 1;
            localStorage.setItem("Ch1Wrong", WrongAns.toString());
            window.location.href = "/gameStart-2";
        }
    }

    let showInfo = false;
    function toggleInfo() {
        showInfo = true;
    }

    function closeInfo() {
        showInfo = false;
    }
</script>

<svelte:head>
    <title>Game</title>
    <meta name="cover" content="cover of game" />
</svelte:head>
<Header>
    <a href="./" style="color: azure;">
        <i class="fa-solid fa-sliders"></i>
    </a>
    <div style="width: 95%;"></div>
    <a style="color: white;margin-right: 15px;" on:click={toggleInfo}>
        <i class="fa-solid fa-circle-question"></i>
    </a>
    <a href="./" style="color: azure;"><i class="fa-solid fa-house"></i></a>
</Header>

<section>
    <div id="container">
        <div id="mask_bg"></div>
        <div class="typewriter">
            {#each text as t, i}
                <p style="animation-delay: {i * 2}s;">{t}</p>
            {/each}
        </div>
        <button id="mail_but" on:click={openMail}>打開密信</button>
    </div>
    <div id="mail">
        <div id="mail_container">
            <div id="mail_text">
                {#each mail_text[random].t as t}
                    <p>{t}</p>
                {/each}
            </div>
            <div id="input_container">
                <input id="ans" placeholder="請輸入地點" bind:value={input} />
                <button on:click={commit}>確定</button>
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
    #container {
        background-color: rgba(0, 0, 0, 0.6);
        padding: 60px;
        z-index: 1;
    }
    section {
        background-image: url("/src/lib/images/P1-Paper.jpg");
        margin: 0;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: -1;
    }

    #mail_but {
        color: azure;
        background-color: cornflowerblue;
        border-radius: 50px;
        /* width: 80px; */
        padding: 7px 5px;
        font-size: 20px;
        float: right;
        margin: 5px;
        outline: none;
    }

    .typewriter p {
        color: aliceblue;
        height: 25px;
        overflow: hidden;
        font-size: 20px;
        word-break: break-all;
        margin: 10px;
        visibility: hidden;
        animation:
            typing 2s steps(40, end),
            appear 1s forwards;
    }

    #mask {
        display: none;
        background-color: rgba(0, 0, 0, 0.6);
        width: 100vw;
        height: 100vh;
        position: absolute;
        top: 0;
        left: 0;
        z-index: 2;
    }

    #mail {
        display: none;
        position: absolute;
        z-index: 3;
        width: 29%;
        height: 75%;
        background-repeat: no-repeat;
        background-image: url("src/lib/images/P5-Mail.png");
    }

    #mail_text {
        /* position: relative; */
        /* top: 150px;
        left: 90px; */
        font-size: 25px;
        font-weight: bold;
        color: rgba(4, 3, 0, 0.738);
        writing-mode: vertical-rl;
    }

    #mail_container {
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 100%;
        justify-content: center;
    }

    #input_container {
        display: flex;
        align-items: center;
        margin-top: 20px;
    }


    /* The typing effect */
    @keyframes typing {
        0% {
            width: 0;
        }
        100% {
            width: 100%;
        }
    }
    @keyframes appear {
        0% {
            visibility: hidden;
        }
        100% {
            visibility: visible;
        }
    }
</style>
