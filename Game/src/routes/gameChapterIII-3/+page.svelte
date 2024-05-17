<script>
    import Anime from "../Anime.svelte";
    const anm = {
      text: [
       " 牆上的話果然是留給同夥的暗示，",
       "你們利用暗示解開大門的鎖後發現，",
       "除了金銀財寶，還有被隱藏在中間的一封密卷，",
       "裡面揭開了一場驚世駭俗的醜事，",
       "裡面詳細記錄了宋徽宗與六賊做的許多荒唐事。"
      ],
      bgimg: "/src/lib/images/P2-DoorOpen.jpg",
      Src: "/gameChapterIX",
      btnText: "下一關",
    };
  </script>
  
  <svelte:head>
    <title>Game</title>
    <meta name="cover" content="cover of game" />
  </svelte:head>
  
  <Anime {...anm} />
  