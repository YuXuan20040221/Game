<script>
    import Header from "../Header.svelte";
    const text = [
        "某日，你收到了一封密信，隱藏在背後的那",
        "個人為了考驗你的真實實力，在信中用了一",
        "個特別的加密方式，提示了你......",
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
            <a href="/gameChapterIX-2" style="color:azure;">打開密信</a>
        </div>
    </div>
</section>

<style>
    #container {
        background-color: rgba(0, 0, 0, 0.6);
        padding: 60px;
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