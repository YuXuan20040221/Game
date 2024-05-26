<script>

    import Header from "../Header.svelte";
    import {onMount} from 'svelte';
    // import GameChapterII2 from "../gameChapterII-2/+page.svelte"

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

    /**
   * @type {HTMLImageElement}
   */
    let img;
    let areas = [
        { shape: 'poly', coords: [210, 290, 210, 650, 260, 640, 300, 640, 300, 270, 260, 280], alt: 'Area 1'},
        { shape: 'poly', coords: [330, 380, 340, 380, 360, 380, 380, 370, 410, 370, 430, 370, 450, 370, 480, 370, 500, 370, 530, 380, 550, 380, 570, 390, 550, 400, 520, 400, 500, 400, 480, 410, 440, 410, 410, 410, 380, 400, 350, 400], alt: 'Area 2'},
        { shape: 'poly', coords: [310, 390, 510, 430, 890, 350, 900, 380, 550, 460, 310, 420], alt: 'Area 3'},
    ];

    function handleClick(){
        alert('aaa');
    }

    let originwidth = 0;
    let originHeight = 0;
    function adjustCoords(){
        let heightRatio = img.clientHeight / originHeight;
        let widthRatio = img.clientWidth / originwidth;

        areas[random].coords = areas[random].coords.map((coord, index) => 
            index % 2 === 0 ? coord * widthRatio : coord * heightRatio
        );

        img.style.display = 'none';
        img.style.display = 'block';
    }
    
    onMount(() => {
        originHeight = img.naturalHeight;
        originwidth = img.naturalWidth;
        adjustCoords();
    });



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
    <img bind:this={img} src="/src/lib/images/P2-Map.jpg" usemap="#image-map" alt="Image Map">

    <map name="image-map">
        <area shape={areas[random].shape} coords={areas[random].coords.join(',')} alt={areas[random].alt} href="/gameChapterII-2">
    </map>
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
        width: 100%;
        height: auto;
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