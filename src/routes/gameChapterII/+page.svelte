<script>
    import Header from "../Header.svelte";
    import { onMount, onDestroy } from "svelte";

    const random = Math.floor(Math.random() * (2 + 1)); //random Int from 0 to 2

    const text = [
        "三人帶著一絲絲的不確定，來到寶藏所在地，",
        "發現寶藏已被重重機關保護。一旦沒有防備",
        "地去觸發機關，大家恐怕都要在這個地方喪",
        "命，此時飛燕大叫了一聲，只見她手裡的密",
        "信背面，在他的反覆摩擦後竟隱約浮現出一",
        "行小字，似乎警告著甚麼......",
    ];

    var mail_text = [
        "村中無水，皆往古月旁汲，日夜不停",
        "你生的如此高大，是否會感到不便?",
        "願與君共享今宵月色",
    ];

    function openMail() {
        // @ts-ignore
        document.getElementById("mail").style.display = "block";
        // @ts-ignore
        document.getElementById("mask").style.display = "block";
    }
    /**
   * @type {{ style: { display: string; }; }}
   */
    let section;
    function closeMail() {
        // @ts-ignore
        document.getElementById("Map").style.display = "block";
        section.style.display = 'none';
    }

    /**
     * @type {HTMLImageElement}
     */
    let image;
    let areas = [
        {
            shape: "rect",
            coords: [
                320, 370, 570, 400
            ],
            alt: "Area 1",
        },
        {
            shape: "rect",
            coords: [
                220, 10, 300, 390
            ],
            alt: "Area 2",
        },
        {
            shape: "rect",
            coords: [
                300, 0, 880, 80
            ],
            alt: "Area 3",
        },
    ];

    // @ts-ignore

    //這邊我想做讓他每個都可以點，然後點到對的就對了
    function handleClick(event, area) {
        if (areas[random] === area) {
            alert("正確");
        } else {
            alert("錯誤");
        }
        event.preventDefault();
    }

    //所以這裡修一下改用each讓他每個都可以調整大小(但我失敗了，幫我)

    // image.onload = function() {
    //     // let heightRatio = img.clientHeight / originHeight;
    //     let widthRatio = image.clientWidth / image.width;

    //     for(var i = 0; i < areas.length; i++){
    //         for(var j = 0; j < areas[i].coords.length; j++){
    //             areas[i].coords[j] *= widthRatio;
    //         }
    //     }
    // }
    let windowWidth = 0;
    let temp = areas;
    function adjustAreaCoords() {
        let widthRatio = windowWidth / image.naturalWidth;

        for(var i = 0; i < areas.length; i++){
            for(var j = 0; j < areas[i].coords.length; j += 2){
                areas[i].coords[j] = temp[i].coords[j] * widthRatio;
            }
        }
        image.style.display = 'none';
        image.style.display = 'block';
    }
    
    onMount(() => {
        // image.onload = () => {
        //     windowWidth = window.innerWidth;
        //     windowHeight = window.innerHeight;
        //     adjustAreaCoords();
        // };
        if (typeof window !== 'undefined') {
            windowWidth = window.innerWidth;

            const handleResize = () => {
                windowWidth = window.innerWidth;

                adjustAreaCoords();
            };

            window.addEventListener('resize', handleResize);

        }
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

<section bind:this={section}>
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
    <img
            bind:this={image}
            src="/src/lib/images/P2-Map.jpg"
            usemap="#image-map"
            alt="Image Map"
    />
    
    <!-- 這個我幹GPT的，可以讓圈起來的地方標顏色 -->
    <svg
        style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none;"
    >
        {#each areas as area}
            <polygon
                points={area.coords.join(",")}
                fill="rgba(255, 0, 0, 0.5)"
                stroke="red"
                stroke-width="1"
            />
        {/each}
    </svg>

    <map name="image-map">
        {#each areas as area (area.alt)}
            <area
                shape={area.shape}
                coords={area.coords.join(",")}
                alt={area.alt}
                on:click|preventDefault={(event) => handleClick(event, area)}

            />
        {/each}
    </map>
</div>

<map name="image-map" id="Map">
    {#each areas as area (area.alt)}
        <area
            shape={area.shape}
            coords={area.coords.join(",")}
            alt={area.alt}
            on:click|preventDefault={(event) => handleClick(event, area)}
        />
    {/each}
</map>

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
        background-image: url("/src/lib/images/P5-Mail.png");
    }

    #mail_text {
        font-size: 15px;
        font-weight: bold;
        color: rgba(4, 3, 0, 0.488);
    }

    #mail_container {
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 100%;
        justify-content: center;
    }

    #mail_container button {
        position: relative;
        top: 20px;
        font-size: 15px;
    }

    #Map {
        display: none;
    }

    #Map img {
        /* position: fixed; */
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
