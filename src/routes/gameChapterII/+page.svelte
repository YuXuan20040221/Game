<script>
    import Header from "../Header.svelte";
    const text = [
        "三人帶著一絲絲的不確定，來到寶藏所在地，",
        "發現寶藏已被重重機關保護。一旦沒有防備",
        "地去觸發機關，大家恐怕都要在這個地方喪",
        "命，此時飛燕大叫了一聲，只見她手裡的密",
        "信背面，在他的反覆摩擦後竟隱約浮現出一",
        "行小字，似乎警告著甚麼......"
    ];

    var animationCompleted = false;

    var input = "";

    var mail_text = "村中無水，皆往古月旁汲，日夜不停";

    function openMail(){
        // @ts-ignore
        document.getElementById('mail').style.display = 'block';
        // @ts-ignore
        document.getElementById('mask').style.display = 'block';
    }

    function closeMail(){
        window.location.href = "/gameChapterII-2";
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
    <a href="./" style="color: azure;"><i class="fa-solid fa-house"></i></a>
</Header>

<section>
    <div id="container">
        <div id="mask"></div>
        <div class="typewriter">
            {#each text as t, i}
                <p style="animation-delay: {i * 2}s;">
                    {t}
                </p>
            {/each}
        </div>
        <button id="mail_but" on:click={openMail}>再次查看密信</button>
        
    </div>
    <div id="mail">
        <div id="mail_container">
            <div id="mail_text">
                {mail_text}
            </div>
            <div>
                <button on:click={closeMail}>前往躲藏地</button>
            </div>
        </div>
    </div>
</section>

<style>
    #container {
        background-color: rgba(0, 0, 0, 0.6);
        padding: 60px;
        z-index: 1;
    }
    section {
        background-image: url("/src/lib/images/P2-Start.jpg");
        margin: 0;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: -1;
    }

    button {
        color: azure;
        background-color: cornflowerblue;
        border-radius: 10px;
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

    #mask{
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
        background-image: url("/src/lib/images/P5-Mail.png");
    }

    #mail_text{
        font-size: 15px;
        font-weight: bold;
        color: rgba(4, 3, 0, 0.488); 

    }

    #mail_container{
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 100%;
        justify-content: center;
    }

    #mail_container button{
        position: relative; 
        top: 20px;
        font-size: 15px;
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