<script>
    import Header from "../Header.svelte";

    const random = Math.floor(Math.random() * (2 + 1)); //random Int from 0 to 2
    const text = [
        "三人帶著一絲絲的不確定，來到寶藏所在地，",
        "發現寶藏已被重重機關保護。一旦沒有防備",
        "地去觸發機關，大家恐怕都要在這個地方喪",
        "命，此時飛燕大叫了一聲，只見她手裡的密",
        "信背面，在他的反覆摩擦後竟隱約浮現出一",
        "行小字，似乎警告著甚麼......"
    ];


    var mail_text = [
        "村中無水，皆往古月旁汲，日夜不停",
        "你生的如此高大，是否會感到不便?",
        "願與君共享今宵月色"
    ];

    function openMail(){
        // @ts-ignore
        document.getElementById('mail').style.display = 'block';
        // @ts-ignore
        document.getElementById('mask').style.display = 'block';
    }

    function closeMail(){
        // @ts-ignore
        document.getElementById('Map').style.display = 'block';

    }


    function handleClick(){
        window.location.href = ('/gameChapterII-2');
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
                {mail_text[random]}
            </div>
            <div>
                <button on:click={closeMail}>前往躲藏地</button>
            </div>
        </div>
    </div>

    
</section>

<div id="Map">
    <img src="/src/lib/images/P2-Map.jpg" usemap="#image-map" alt="Image Map">

    <button id="button{random}" on:click={handleClick}></button>
    <!-- <button id="button1" on:click={handleClick}></button>
    <button id="button2" on:click={handleClick}></button> -->

    <!-- <map name="image-map">
        <area shape={areas[random].shape} coords={areas[random].coords.join(',')} alt={areas[random].alt} href="/gameChapterII-2">
    </map> -->
</div>


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

    #Map{
        display: none;
    }

    #Map img{
        position: fixed;
        width: 100%;
        height: 100%;
        z-index: 2;
    }

    #button0{
        position: absolute;
        top: 63%;
        right: 43%;
        width: 25%;
        height: 7%;
        z-index: 5;
        background-color: transparent;
        border: 0 transparent;
    }

    #button1{
        position: absolute;
        right: 70%;
        width: 10%;
        height: 70%;
        z-index: 5;
        background-color: transparent;
        border: 0 transparent;
    }

    #button2{
        position: absolute;
        top: 10%;
        right: 0%;
        width: 70%;
        height: 10%;
        z-index: 5;
        background-color: transparent;
        border: 0 transparent;
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