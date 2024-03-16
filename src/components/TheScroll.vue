<template>
  <div class="scroll-wrapper">
    <div class="zoom-container">
      <div class="page a">
        <p>第一页</p>
        <div class="clr"></div>
      </div>
      <div class="page b">
        <p>第二页</p>
        <div class="clr"></div>
      </div>
      <div class="page c">
        <p>第三页</p>
        <div class="clr"></div>
      </div>
      <div class="page d">
        <p>第四页</p>
        <div class="clr"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, computed, defineProps } from "vue";

const props = defineProps({});

let isMobile = computed(() => {
  return /iPhone|iPad|iPod|iOS|Android/i.test(navigator.userAgent);
});

onMounted(() => {
  const container = document.querySelector(".scroll-wrapper .zoom-container");
  const pages = document.querySelectorAll(".page");
  const wrapper = document.querySelector(".scroll-wrapper");

  wrapper.style.setProperty("--_number-of-pages", pages.length);
  // for mobile devide the scale is triggered at a specific y position
  if (isMobile.value) {
    container.style.transition = "all 0.3s linear";
  }
  // get the offset of the container before sticking
  let initialOffset =
    parseInt(getComputedStyle(container).marginTop) + wrapper.offsetTop;

  const distanceForZoom = parseInt(
    getComputedStyle(wrapper).getPropertyValue("--_zoom-height")
  );
  const numberOfPages = parseInt(
    getComputedStyle(wrapper).getPropertyValue("--_number-of-pages")
  );

  window.addEventListener("resize", () => {
    initialOffset =
      parseInt(getComputedStyle(container).marginTop) + wrapper.offsetTop;
  });

  document.addEventListener("scroll", () => {
    scaleContainer(initialOffset, distanceForZoom);
    clipPath(initialOffset + distanceForZoom, numberOfPages);
  });
});

function clipPath(startingOffset, numberOfPages, distanceForZoom) {
  // allowance for fast scrolling
  const allowance = 400;

  if (
    window.scrollY < startingOffset - 400 ||
    window.scrollY > startingOffset + numberOfPages * window.innerHeight + 400
  ) {
    return;
  }
  const pages = document.querySelectorAll(".page");
  for (let i = 1; i < pages.length; i++) {
    const page = pages[i];
    page.style.clipPath = `inset(${
      ((window.scrollY - startingOffset - i * window.innerHeight) /
        window.innerHeight) *
      -100
    }% 0 0 0)`;
  }

  console.log(
    window.scrollY - startingOffset,
    window.innerHeight,
    container.offsetHeight
  );
}

function scaleContainer(initialOffset, distanceForZoom) {
  const container = document.querySelector(".scroll-wrapper .zoom-container");

  const scrollPercentage = Math.max(
    Math.min((window.scrollY - initialOffset) / distanceForZoom, 1),
    0
  );

  // apply styles
  if (scrollPercentage == 0) {
    container.style.boxShadow = "0 0 1.5rem rgba(0, 0, 0, 0.321)";
    container.style.borderRadius = "2rem";
  } else if (scrollPercentage == 1) {
    container.style.boxShadow = "none";
    container.style.borderRadius = "0rem";
  } else {
    container.style.boxShadow = "0 0 1.5rem rgba(0, 0, 0, 0.321)";
    container.style.borderRadius = "2rem";
  }

  // apply scale
  if (isMobile.value) {
    container.style.setProperty(
      "--_scroll-percentage",
      scrollPercentage > 0.15 ? 1 : 0
    );
  } else {
    container.style.setProperty("--_scroll-percentage", scrollPercentage);
  }
}
</script>

<style scoped>
.scroll-wrapper {
  /* must be in px */
  --_zoom-height: 300px;

  /* controll by js */
  --_scroll-percentage: 1;
  --_number-of-pages: 4;

  min-height: calc(var(--_number-of-pages) * 100dvh + var(--_zoom-height));
  margin-top: 10rem;
  display: flex;
  flex-direction: column;
}

.zoom-container {
  scale: calc((70 + 30 * clamp(0, var(--_scroll-percentage), 1)) / 100);
  border-radius: 2rem;
  transition: scale 0.1s linear, border-radius 0.2s linear;
  box-shadow: 0 0 1.5rem rgba(0, 0, 0, 0.321);
  position: sticky;
  height: 100dvh;
  top: 0;
  overflow: hidden;
}

.page {
  position: absolute;
  inset: 0;
  height: 100dvh;
  width: 100%;
}
.page:not(:first-child) {
  clip-path: inset(100% 0 0 0);
}

.page {
  --_clr: #ce50b5;
  display: grid;
  place-items: center;
  grid-template-columns: 1fr 1fr;
}

p {
  text-align: center;
  font-size: 5em;
  background-color: white;
  outline: 5px solid var(--_clr);
  padding: 1rem 2rem;
  border-radius: 3rem;
}

.clr {
  background-color: var(--_clr);
  width: 100%;
  height: 100%;
}

.a {
  --_clr: var(--clr-red);
}
.b {
  --_clr: var(--clr-purple);
}
.c {
  --_clr: var(--clr-blue);
}
.d {
  --_clr: #b6bd58;
}

@media screen and (max-width: 700px) {
  .page {
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr;
  }
}
</style>
