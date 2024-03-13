<template>
  <div class="wrapper">
    <div class="container">
      <div class="item">
        <div class="row">
          <img src="@/assets/imgs/fire.png" alt="" width="100" height="100" />
          <p>热榜</p>
        </div>
        <p class="desc">随时随地, 紧追校园热点</p>
      </div>
      <div class="item">
        <div class="row">
          <img src="@/assets/imgs/clock.png" alt="" width="100" height="100" />
          <p>时间轴</p>
        </div>
        <p class="desc">不会错过任何新鲜事!</p>
      </div>
      <div class="item">
        <div class="row">
          <img src="@/assets/imgs/phone.png" alt="" width="100" height="100" />
          <p>最新评论</p>
        </div>
        <p class="desc">大家都在讨论什么👀</p>
      </div>
      <h2>
        想怎么刷?&nbsp;&nbsp;&nbsp;&nbsp;<br />&nbsp;&nbsp;&nbsp;&nbsp;就这么刷!
      </h2>
      <div class="item">
        <div class="row">
          <img src="@/assets/imgs/pie.png" alt="" width="100" height="100" />
          <p>超多分区</p>
        </div>
        <p class="desc">找到你感兴趣的话题吧</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, defineProps } from "vue";

const props = defineProps({});
</script>

<style scoped>
.wrapper {
  padding-block: 15vh;
  padding-block: 15svh;
  padding-inline: var(--page-padding-inline);
}

.container {
  --_row-height: 10rem;

  border: 5px solid black;
  border-radius: 3rem;
  padding: 3rem 5rem;

  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: 1fr 1fr;
  gap: 1rem;
}

img {
  max-height: var(--_row-height);
  width: auto;
  object-fit: contain;
  object-position: left;
}

.row {
  position: relative;
  display: inline-block;
  font-weight: 900;
}

.row p {
  position: absolute;
  bottom: 10%;
  left: 70%;
  width: max-content;
  font-size: var(--fs-800);
}

.desc {
  font-size: var(--fs-400);
  margin-left: 1.5ch;
  margin-block: 1rem;
}

h2 {
  grid-column: 1 / 3;
  text-align: center;
  font-size: 5em;
  font-weight: 900;
}

@media screen and (max-width: 1200px) {
  .container {
    grid-template-columns: 1fr 1fr;
    grid-template-rows: repeat(3, 1fr);
  }
  h2 {
    grid-row: 2 / 3;
    font-size: 4em;
  }
  .item {
    text-align: center;
  }
}

@media screen and (max-width: 700px) {
  .container {
    --_row-height: 15rem;
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: repeat(4, 1fr);
    place-items: center;
  }
  .row p {
    font-size: var(--fs-900);
  }
  .desc {
    font-size: var(--fs-500);
  }
  h2 {
    font-size: 3.3em;
    grid-column: unset;
    grid-row: 3 / 4;
  }
}
</style>
