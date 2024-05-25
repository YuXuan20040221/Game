<script>
  import Header from "../Header.svelte";
  const wrong = ["Ch1Wrong", "Ch2Wrong", "Ch3Wrong", "Ch4Wrong", "Ch5Wrong"];
  const hf = ["/gameStart","/gameChapterII","/gameChapterIII","/gameChapterIX","/gameChapterX"]
  var level = [0, 0, 0, 0, 0];
  for (let i = 0; i < 5; i++) {
    // @ts-ignore
    if (localStorage.getItem(wrong[i]) <= 0) {
      level[i] = 0;
      // @ts-ignore
    } else if (localStorage.getItem(wrong[i]) <= 1) {
      level[i] = 3;
      // @ts-ignore
    } else if (localStorage.getItem(wrong[i]) <= 3) {
      level[i] = 2;
    } else {
      level[i] = 1;
    }
  }
</script>

<svelte:head>
  <title>Game Menu</title>
  <meta name="description" content="About this app" />
</svelte:head>
<Header>
  <span
    ><a href="./" style="color: white;"><i class="fa-solid fa-house"></i></a
    ></span
  >
</Header>

<section>
  <div id="container">
    <div id="title_container">
      <div>遊戲選單</div>
    </div>

      {#each level as l, i}
        <a id="game_{i}" class="game" href={hf[i-1]}>
          <div>關卡 {++i}</div>
          <div>
            {#if l == 3}
              <i class="fa-solid fa-star"></i>
              <i class="fa-solid fa-star"></i>
              <i class="fa-solid fa-star"></i>
              <br>通關成功
            {:else if l == 2}
              <i class="fa-solid fa-star"></i>
              <i class="fa-solid fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <br>通關成功
            {:else if l == 1}
              <i class="fa-solid fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <br>通關成功
            {:else}
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <i class="fa-regular fa-star"></i>
              <br>未通關
            {/if}
          </div>
        </a>
      {/each}
</section>

<style>
  section {
    background-image: url("/src/lib/images/MainPage1.jpg");
  }

  #container {
    background-color: white;
    /* opacity: 0.8; */
    display: grid;
    grid-template-rows: 30px auto auto;
    grid-template-columns: 33% 33% 33%;
    align-items: center;
    width: 60%;
  }

  #title_container {
    display: flex;
    grid-column: 1/4;
    justify-content: center;
    font-size: 30px;
    margin-top: 20px;
  }

  .game {
    background-color: rgb(254, 254, 196);
    margin: 30px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 20px;
    flex: 0,0,20%;
  }

  .fa-solid.fa-star,
  .fa-regular.fa-star {
    color: gold;
  }
</style>
