<script>
    import Header from "../Header.svelte";

    const text = [
        "從門縫一查看，",
        "發現了許多金銀財寶，確信了信中所述，",
        "但門被上了鎖，而門旁的石牆上出現了這樣的圖畫......"
    ];
</script>

<Header>
    <span>
        <a href="./" style="color: white;">
            <i class="fa-solid fa-sliders"></i>
          </a>
          <a href="./" style="color: white;">
            <i class="fa-solid fa-house"></i>
          </a>
    </span>
</Header>

<section>
    <!-- <img src="/src/lib/images/P2-DoorClose.jpg" alt="door"> -->
    <div id="container">
        <div class="typewriter">
            {#each text as t, i}
                <p style="animation-delay: {i * 2}s;">{t}</p>
            {/each}
        </div>
        <div id='locker'><a href="/p3Pw">點擊密碼鎖</a></div>
    </div>
    
</section>

<style>
    section{
        background-image: url("/src/lib/images/P2-DoorClose.jpg");
        height:50px; 
    }

    #locker{
        border-radius: 5px;
        color:white;
        background-color:lightgray;
        padding: 10px;
        font-size: 20px;
        z-index: 1; 
		position: absolute; 
		top: 410px;
		left: 700px;
    }
    a{
        text-decoration: none;
    }
    #container {
        background-color: rgba(0, 0, 0, 0.6);
        padding: 60px;
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
