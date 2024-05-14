<script>
    import Header from "../Header.svelte";
</script>

<Header>
    <link rel="stylesheet" type="text/css" href="../style.css">
    <span><a href="./" style="color: azure;"><i class="fa-solid fa-house"></i></a></span>
</Header>

<section>
    <video
        autoplay
        style="width:100%;"
        id="openVideo">
        <source src="\src\lib\images\Start.mp4" type="video/mp4" />
        <track
            kind="captions"
            src="captions.vtt"
            srclang="en"
            label="English"
            default
        />
    </video>

</section>
