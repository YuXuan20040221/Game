<script>
    import Header from "../Header.svelte";
    const text = [
        "在看完這封密卷後，在你的慎重思考後，",
        "決定在明晚將其送去給當時的好友陳東。",
        "但就在你們正準備要回去時，飛燕突然誤",
        "觸了陷阱，瞬間整間屋子充滿大火，這時",
        "你也發現了門被另一道鎖鎖住了，鎖頭上",
        "刻著密密麻麻的小字，貌似是首詩，在火",
        "勢一發不可收拾前，你需要找出鑰匙，才",
        "有可能逃離這裡，安全離開這裡並把密卷",
        "送出。在你們三人的合作下，找出了這樣",
        "的箱子......",
    ];
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
    <a href="./" style="color: azure;"><i class="fa-solid fa-house"></i></a>
</Header>

<section>
    <div id="container">
        <div class="typewriter">
            {#each text as t, i}
                <p style="animation-delay: {i * 2}s;">{t}</p>
            {/each}
        </div>
        <div id="lock" style="float: right; margin:5px">
            <a href="/gameChapterIX-2" style="color:azure;">查看箱子</a>
        </div>
    </div>
</section>

<style>
    #container {
        background-color: rgba(0, 0, 0, 0.6);
        padding: 60px;
    }
    section {
        background-image: url("/src/lib/images/P4-Fire2.jpg");
    }

    #lock {
        color: azure;
        background-color: cornflowerblue;
        border-radius: 50px;
        width: 80px;
        padding: 10px;
        font-size: 20px;
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
