<template>
  <main>
    <!-- <div class="landing-background"></div> -->
    <TheLanding />
    <TheIntroduction />
    <TheFeatures />
  </main>
</template>

<script setup>
import TheLanding from "@/components/TheLanding.vue";
import TheIntroduction from "./components/TheIntroduction.vue";

import TheFeatures from "./components/TheFeatures.vue";

document.addEventListener("touchstart", function () {}, true);
</script>

<style scoped>
main {
  background-color: var(--clr-background);
}

.landing-background {
  position: absolute;
  z-index: 0;
  inset: 0;
  height: 115vh;
  height: 115svh;

  mask-image: linear-gradient(180deg, #ffffff 77%, #ffffff00 100%);

  background-size: 100% 100%;
  background-position: 0px 0px, 0px 0px, 0px 0px, 0px 0px;
  background-image: radial-gradient(
      84% 64% at -28% 91%,
      #eeb19aff 15%,
      #f4c39a00 80%
    ),
    radial-gradient(82% 60% at 100% 100%, #ffffff 0%, #ffffff00 100%),
    radial-gradient(142% 56% at 106% -10%, #85daf6ff 8%, #b1e4ea0a 100%),
    linear-gradient(90deg, #f6afd9ff 6%, #d4aaefff 51%, #b1e4ea 96%);
}
</style>
