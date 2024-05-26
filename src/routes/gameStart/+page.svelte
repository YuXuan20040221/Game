<script>
    import Header from "../Header.svelte";
    import Information from "../Information.svelte";

    const text = [
        "某日，你收到了一封密信，隱藏在背後的那",
        "個人為了考驗你的真實實力，在信中用了一",
        "個特別的加密方式，似乎是在指引了一個神",
        "秘寶藏的埋藏地點......"
    ];

    const mail_text = [
        "樺樹林裡無木，",
        "木在田中，",
        "閒人窗紗掩月，",
        "取刀一剪。"
    ]

    const info = {
        text: [
        "密碼學：析字法",
        "解密：在信中只有幾個字，要拆解字的意思(eg.青=十二月)",
        ],
    };

    var input = "";

    function openMail(){
        // @ts-ignore
        document.getElementById('mail').style.display = 'block';
        // @ts-ignore
        document.getElementById('mask').style.display = 'block';
    }

    function commit(){
        if(input != "華東門前"){
            alert("答案錯誤!");
        }
        else{
            window.location.href = "/gameStart-2";
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
</svelte:head>
<Header>
    <a href="./" style="color: azure;">
        <i class="fa-solid fa-sliders"></i>
    </a>
    <div style="width: 95%;"></div>
    <a
    style="color: white;margin-right: 5px;"
    on:click= {toggleInfo}
  >
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
                {#each mail_text as t}
                    <p>{t}</p>
                {/each}
            </div>
            <div style="display: flex;">
                <input id="ans" placeholder="請輸入地點" bind:value={input}>
                <button on:click={commit}>確定</button>
            </div>
        </div>
    </div>
    
</section>

{#if showInfo}
    <div id="info">
        <Information {...info} close={closeInfo}/>
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

    #mask_bg{
        display: none;
        background-color: rgba(0, 0, 0, 0.6);
        width: 100vw;
        height: 100vh;
        position: absolute;
        top: 0;
        left: 0;
        z-index: 2;
        
    }

    #mail{
        display: none;
        position: absolute;
        z-index: 3;
        width: 29%;
        height: 75%;
        background-repeat: no-repeat;
        background-image: url("src/lib/images/P5-Mail.png");
    }

    #mail_text{
        /* position: relative; */
        /* top: 150px;
        left: 90px; */
        font-size: 25px;
        font-weight: bold;
        color: rgba(4, 3, 0, 0.738);
        writing-mode: vertical-rl;   
    }

    #mail_container{
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 100%;
        justify-content: center;
    }

    #mail_container input{
        position: relative;
        top: 50px;
        border: transparent;
        border-radius: 10px;
        padding: 10px;
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