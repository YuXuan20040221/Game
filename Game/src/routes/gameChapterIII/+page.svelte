<script>
    import Header from "../Header.svelte";
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
    <img src="/src/lib/images/P2-DoorClose.jpg" alt="door">
    <div id='locker'><a href="/p3Pw">點擊密碼鎖</a></div>
</section>

<style>
    section{
        background-color: rgba(130, 92, 69, 0.79);
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
		top: 400px;
		left: 700px;
    }
    a{
        text-decoration: none;
    }
</style>
