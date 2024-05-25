<script>
    import Header from "../Header.svelte";
    import {onMount} from "svelte"
    import 'image-map-resizer';

    function commit(){
        alert("aaa");
    }

    onMount(() => {
        $('map').imageMapResize();
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
    <div>
       <img src="/src/lib/images/P2-Map.jpg" usemap="#img_map" id="map" alt="">
       <map name="img_map">
            <!-- <area shape="polygon" coords="330, 380, 340, 380, 360, 380, 380, 370, 410, 370, 430, 370, 450, 370, 480, 370, 500, 370, 530, 380, 550, 380, 570, 390, 550, 400, 520, 400, 500, 400, 480, 410, 440, 410, 410, 410, 380, 400, 350, 400" href="https://chatgpt.com/?oai-dm=1"> -->
            <area shape="rect" coords="250, 300, 650, 550" href="https://chatgpt.com/?oai-dm=1">
       </map>     
    </div>
 
</section>

<style>

    section {
        /* background-image: url("");
        background-size: cover; */
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


    #map{
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
    }

</style>