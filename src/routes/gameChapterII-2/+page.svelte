<script>
    import Anime from "../Anime.svelte";
    
    const anm = {
      text: [
        "按照密信裡給予的線索險象環生的躲過了陷阱，",
        "走到了門前，門後透出一抹奇異的金黃色光芒......",
      ],
      bgimg: "/src/lib/images/P2-DoorOpen.jpg",
      Src: "/gameChapterIII",
      btnText: "下一關",
    };
  </script>
  
  <svelte:head>
    <title>Game</title>
    <meta name="cover" content="cover of game" />
  </svelte:head>
  
  <Anime {...anm} />
  