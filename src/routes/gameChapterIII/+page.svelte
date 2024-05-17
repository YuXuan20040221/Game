<script>
  import Anime from "../Anime.svelte";
  const anm = {
    text: [
      "從門縫一查看，",
      "發現了許多金銀財寶，確信了信中所述，",
      "但門被上了鎖，而門旁的石牆上出現了這樣的圖畫......",
      "-------------------------------------------------------------------------",
      "密碼學：反切法",
      "說明：上字的韻母加下字的聲母和聲調"
    ],
    bgimg: "/src/lib/images/P2-DoorClose.jpg",
    Src: "/gameChapterIII-2",
    btnText: "點擊密碼鎖",
  };
</script>

<svelte:head>
  <title>Game</title>
  <meta name="cover" content="cover of game" />
</svelte:head>

<Anime {...anm} />
