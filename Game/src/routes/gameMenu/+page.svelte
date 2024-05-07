<svelte:head>
  <title>Game Menu</title>
  <meta name="description" content="About this app" />
  <script src="https://kit.fontawesome.com/86e57103de.js" crossorigin="anonymous"></script>
  <i class="fa-solid fa-house"></i>
</svelte:head>

<section>
  <div id="container">

	<div id="title_container">
		<div>遊戲選單</div>
	</div>
	
    <div id="button_container_top">
      <div id="game_all" class="game">
        <div>全關卡</div>
        <div>
          <i class="fa-solid fa-star"></i>
          <i class="fa-solid fa-star"></i>
          <i class="fa-solid fa-star"></i>
        </div>
        <div>尚未遊玩</div>
      </div>

      <div id="game_1" class="game">
        <div>關卡 1</div>
        <div>
          <i class="fa-solid fa-star"></i>
          <i class="fa-solid fa-star"></i>
          <i class="fa-solid fa-star"></i>
        </div>
        <div >最佳成績</div>
      </div>

      <div id="game_2" class="game">
        <div>關卡 2</div>
        <div>
          <i class="fa-regular fa-star"></i>
          <i class="fa-regular fa-star"></i>
          <i class="fa-regular fa-star"></i>
        </div>
        <div>最佳成績</div>
      </div>
    </div>

	<div id="button_container_down">
		<div id="game_3" class="game">
			<div>關卡 3</div>
			<div>
			  <i class="fa-regular fa-star"></i>
			  <i class="fa-regular fa-star"></i>
			  <i class="fa-regular fa-star"></i>
			</div>
			<div>尚未遊玩</div>
		  </div>
	
		  <div id="game_4" class="game">
			<div>關卡 4</div>
			<div>
			  <i class="fa-regular fa-star"></i>
			  <i class="fa-regular fa-star"></i>
			  <i class="fa-regular fa-star"></i>
			</div>
			<div>失敗</div>
		  </div>
	
		  <div id="game_5" class="game">
			<div>關卡 5</div>
			<div>
			  <i class="fa-regular fa-star"></i>
			  <i class="fa-regular fa-star"></i>
			  <i class="fa-regular fa-star"></i>
			</div>
			<div>尚未遊玩</div>
		  </div>
	</div>
  </div>
</section>

<style>
  section {
    background-image: url("/src/lib/images/menu_bg.jpg");
  }

  #container {
    background-color: azure;
    /* opacity: 0.8; */
	display:flex;
	flex-direction: column;
    align-items: center;
  }

  #title_container{
	display: flex;
	justify-content: center;
	font-size: 30px;
	margin-top:20px;
  }

  #button_container_top{
	display: flex;
  }

  #button_container_down{
	display: flex;
  }

  .game{
	background-color:rgb(254, 254, 196);
	margin: 30px;
	padding: 20px;
	display:flex;
	flex-direction: column;
    align-items: center;
	border-radius: 20px;
  }

  .fa-solid.fa-star, .fa-regular.fa-star{
	color:gold;
  }
</style>
