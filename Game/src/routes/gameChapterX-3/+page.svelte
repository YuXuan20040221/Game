<script>
    import Anime from "../Anime.svelte";
    const anm = {
      text: [
        "解開後，信中約了時間與地點，你依約抵達了那個地方，",
        "發現，原來此位隱藏在背後的人就是好友陳東，",
        "他告訴了你寶藏的真相與六賊貪贓枉法的內幕，",
        "請求你將密卷交給他，讓他上書請誅六賊。"

      ],
      bgimg: "/src/lib/images/P5-End2.jpg",
      Src: "/gameEnd",
      btnText: "結局",
    };
  </script>
  
  <svelte:head>
    <title>Game</title>
    <meta name="cover" content="cover of game" />
  </svelte:head>
  
  <Anime {...anm} />
  