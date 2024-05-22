<script>
  import Header from "../Header.svelte";

  const text1 = ["割", "節", "施"];
  const text2 = ["水", "蛙", "土"];
  const text3 = ["哥", "瓜", "想"];
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
      alert("答錯了QQ");
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
      <div>
        <img src="/src/lib/images/P3-frog.jpg" alt="question" />
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
