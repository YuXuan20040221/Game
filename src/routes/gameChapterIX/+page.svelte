<script>
  import Anime from "../Anime.svelte";
  const anm = {
    text: [
      "在看完這封密卷後，在你的慎重思考後，",
      "決定在明晚將其送去給當時的好友陳東。",
      "但就在你們正準備要回去時，飛燕突然誤",
      "觸了陷阱，瞬間整間屋子充滿大火，這時",
      "你也發現了門被另一道鎖鎖住了，鎖頭上",
      "刻著密密麻麻的小字，貌似是首詩，在火",
      "勢一發不可收拾前，你需要找出鑰匙，才",
      "有可能逃離這裡，安全離開這裡並把密卷",
      "送出。在你們三人的合作下，找出了這樣",
      "的箱子......",
      "----------------------------------------",
      "密碼學：藏頭詩",
      "說明：每一句最後一字含有下一行第一個字"
    ],
    bgimg: "/src/lib/images/P4-Fire2.jpg",
    Src: "/gameChapterIX-2",
    btnText: "查看箱子",
  };
</script>

<svelte:head>
  <title>Game</title>
  <meta name="cover" content="cover of game" />
</svelte:head>

<Anime {...anm} />