<template>
  <div class="wrapper">
    <p class="title">Triple Uni</p>
    <h2>
      <span>来自三校的我们</span><span class="comma">, </span
      ><span>心声共鸣</span>
    </h2>
    <div class="flex">
      <p>
        Triple Uni 是接通 "HKU噗噗"、"马料水哔哔机" 及 "Stardust科大星尘"
        三校匿名树洞的社交平台，旨在打造港校交流的小宇宙，你将在这里观测到每一颗行星间的碰撞交流～
      </p>
      <img
        src="@/assets/imgs/U.png"
        alt="Triple Uni Logo"
        width="300"
        height="300"
        class="logo"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, defineProps } from "vue";

const props = defineProps({});
</script>

<style scoped>
.wrapper {
  padding-block: 5vh;
  padding-block: 5svh;
  padding-inline: var(--page-padding-inline);
}

.title {
  font-size: var(--fs-800);
  font-weight: 700;
  margin-bottom: 1rem;
}

h2 {
  font-size: var(--fs-900);
  margin-bottom: 5rem;
}

.flex {
  display: flex;
  gap: 2rem;
  justify-content: space-between;
}

.logo {
  max-width: 30%;
  flex-grow: 0;
}

p {
  font-size: var(--fs-500);
  line-height: 1.5;
  max-width: 50ch;
}

@media screen and (max-width: 700px) {
  .flex {
    flex-direction: column;
    align-items: center;
  }
  .logo {
    max-width: 40%;
  }
  h2 {
    margin-bottom: 3rem;
  }
  h2 span {
    display: block;
  }
  .comma {
    display: none;
  }
}
</style>
