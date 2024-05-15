<script>
    import Anime from "../Anime.svelte";
    const anm = {
      text: [
       " 你順利找到鑰匙，逃離了火場。"
      ],
      bgimg: "/src/lib/images/P4-Fire.jpg",
      Src: "/gameChapterX",
      btnText: "下一關",
    };
  </script>
  
  <svelte:head>
    <title>Game</title>
    <meta name="cover" content="cover of game" />
  </svelte:head>
  
  <Anime {...anm} />
  