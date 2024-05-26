<script>
  import Header from "../Header.svelte";

  let random = Math.floor(Math.random() * 4);
  const text = [
    {t1: ["割", "節", "施"], t2: ["水", "蛙", "土"], t3: ["哥", "瓜", "想"], src: "/src/lib/images/P3-frog.jpg"},
    {t1: ["喝", "節", "施"], t2: ["水", "我", "土"], t3: ["哥", "火", "想"], src: "/src/lib/images/P3-Drink.png"},
    {t1: ["住", "節", "施"], t2: ["水", "願", "土"], t3: ["哥", "站", "想"], src: "/src/lib/images/P3-Hospital.jpg"},
    {t1: ["呼", "節", "施"], t2: ["水", "陶", "土"], t3: ["哥", "豪", "想"], src: "/src/lib/images/P3-Flower.jpg"}
];

  const text1 = text[random].t1;
  const text2 = text[random].t2;
  const text3 = text[random].t3;
  let count = [0, 0, 0];
  let WrongAns = 0;
  //   const ans = ["割", "蛙", "瓜"];

  // @ts-ignore
  function change(i) {
    count[i] = (count[i] + 1) % 3;
  }

  function checkAns() {
    if (count[0] == 0 && count[1] == 1 && count[2] == 1) {
      WrongAns+=1;
      localStorage.setItem("Ch3Wrong", WrongAns.toString());
      window.location.href = "/gameChapterIII-3";
    } else {
      alert("答錯了");
      WrongAns+=1;
      localStorage.setItem("Ch3Wrong", WrongAns.toString());
    }
  }

  
</script>

<Header>
  <a href="/gameMenu" style="color: white;">
    <i class="fa-solid fa-sliders"></i>
  </a>
  <div style="width: 95%;"></div>
  <a href="./" style="color: white;">
    <i class="fa-solid fa-house"></i>
  </a>
</Header>

<section>
  <div id="allContainer">
    <div id="container">
      <div style="padding: 10px;">
        <img src={text[random].src} alt="question" style="width: 259px;"/>
      </div>

      <div id="lockerImg">
        <img src="/src/lib/images/P3-Locker.png" alt="locker" />
      </div>
    </div>

    <button id="lockerButton" on:click={() => checkAns()}>開鎖</button>
    <button on:click={() => change(0)} class="ansBlock" style="left: 590px;"
      >{text1[count[0]]}</button
    >
    <button on:click={() => change(1)} class="ansBlock" style="left: 687px;"
      >{text2[count[1]]}</button
    >
    <button on:click={() => change(2)} class="ansBlock" style="left: 785px;"
      >{text3[count[2]]}</button
    >
  </div>

</section>

<style>
  section {
    background-image: url("/src/lib/images/P2-DoorOpen.jpg");
    /* opacity: 0.5; */
  }

  #container {
    background-color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  #lockerButton {
    border-radius: 5px;
    /* color: gold; */
    background-color: lightgoldenrodyellow;
    padding: 10px;
    font-size: 20px;
    margin-left: 10px;
  }

  #lockerImg {
    padding: 10px;
  }

  #allContainer {
    display: flex;
    align-items: flex-end;
  }

  .ansBlock {
    font-size: 70px;
    position: absolute;
    top: 503px;
  }
</style>
