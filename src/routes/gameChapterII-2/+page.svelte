<script>
// @ts-nocheck

    import Header from "../Header.svelte";
    import {onMount} from "svelte"
    // import 'image-map-resizer';

    function commit(){
        alert("aaa");
    }

    /**
   * @type {HTMLImageElement}
   */
    let img;
    let areas = [
        // { shape: 'rect', coords: [34, 44, 270, 350], href: 'https://example.com/area1', alt: 'Area 1' },
        // { shape: 'circle', coords: [337, 300, 44], href: 'https://example.com/area2', alt: 'Area 2' },
        { shape: 'poly', coords: [330, 380, 340, 380, 360, 380, 380, 370, 410, 370, 430, 370, 450, 370, 480, 370, 500, 370, 530, 380, 550, 380, 570, 390, 550, 400, 520, 400, 500, 400, 480, 410, 440, 410, 410, 410, 380, 400, 350, 400], href: '#', alt: 'Area 3' }
    ];
    
    let originalWidth = 0;
    let originalHeight = 0;

    function adjustCoords() {
        const widthRatio = img.clientWidth / originalWidth;
        const heightRatio = img.clientHeight / originalHeight;
        
        areas.forEach(area => {
        // @ts-ignore
        area.adjustedCoords = area.coords.map((coord, index) => 
            index % 2 === 0 ? coord * widthRatio : coord * heightRatio
        ).join(',');
        });
    }

    onMount(async () => {
        if(typeof window !== 'undefined'){
            img = document.getElementById('img');
            const { default: imageMapResize } = await import('image-map-resizer');
            imageMapResize();

            img.onload = () => {
                originalWidth = img.naturalWidth;
                originalHeight = img.naturalHeight;
                adjustCoords();
            };

            window.addEventListener('resize', adjustCoords);
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

<section>
    <!-- <div>
       <img src="/src/lib/images/P2-Map.jpg" usemap="#img_map" id="map" alt="">
       <map name="img_map">
            <area shape="polygon" coords="330, 380, 340, 380, 360, 380, 380, 370, 410, 370, 430, 370, 450, 370, 480, 370, 500, 370, 530, 380, 550, 380, 570, 390, 550, 400, 520, 400, 500, 400, 480, 410, 440, 410, 410, 410, 380, 400, 350, 400" href="https://chatgpt.com/?oai-dm=1">
            <area shape="rect" coords="250, 300, 650, 550" href="https://chatgpt.com/?oai-dm=1">
       </map>     
    </div> -->

    <img bind:this={img} id="img" src="/src/lib/images/P2-Map.jpg" usemap="#image-map" alt="Image Map Example" on:load={adjustCoords}>

    <map name="image-map">
        {#each areas as area}
            <area shape={area.shape} coords={area.adjustedCoords} href={area.href} alt={area.alt}>
        {/each}
    </map>
 
</section>

<style>

    section {
        /* background-image: url("");
        background-size: cover; */
    }

    img {
        width: 100%;
        height: auto;
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