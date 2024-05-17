<script>
    import Anime from "../Anime.svelte";
    const anm = {
      text: [
        "逃離後，你帶著財寶回到家，發現家中好像有人進入過，",
        "在翻找一番後，你發現並未有東西遺失，但卻多了一封信件， ",
        "你發現了熟悉的章印，得知這封信應該就是當時告知你寶藏訊息的人，",
        "但這次卻不是使用上次的加密方式。",
        "------------------------------------------------------------",
        "密碼學：字驗",
        "說明：由題目找到劃記的字是第幾個字，再對應字驗該字在第幾個，",
        "最後可得到對照表對應的第幾行第幾字，即可找出XX地點的X方，X時集合"
      ],
      bgimg: "/src/lib/images/P5-House.jpg",
      Src: "/gameChapterX-2",
      btnText: "點擊信件",
    };
  </script>
  
  <svelte:head>
    <title>Game</title>
    <meta name="cover" content="cover of game" />
  </svelte:head>
  
  <Anime {...anm} />
  