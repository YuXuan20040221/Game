<script>
// @ts-nocheck

    import Header from "../Header.svelte";
    import {onMount} from 'svelte';
    export let random;

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
        ).join(',');

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

    <img bind:this={img} src="/src/lib/images/P2-Map.jpg" usemap="#image-map" alt="Image Map">

    <map name="image-map" on:click|preventDefault={handleClick}>
        <area shape={areas[random].shape} coords={areas[random].coords} alt={areas[random].alt}>
    </map>
 
</section>

<style>

    img {
        width: 100%;
        height: auto;
    }


</style>