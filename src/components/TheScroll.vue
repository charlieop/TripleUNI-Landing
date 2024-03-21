<template>
  <div class="scroll-wrapper">
    <div class="zoom-container">
      <div class="page a">
        <div class="text">
          <p class="title">说你想说</p>
          <p class="desc">
            想法？经验？<br />
            牢骚？喜悦？<br /><br />
            想说什么，匿名告诉大家吧！
          </p>
        </div>
        <div class="img">
          <p class="new">分享</p>

          <div class="img-background-wrapper">
            <div class="img-background"></div>
          </div>
          <img
            class="content"
            src="https://picsum.photos/id/27/200/300"
            alt="function display"
          />
          <img
            class="frame"
            src="@/assets/imgs/iphone15.webp"
            alt="phone frame"
          />
        </div>
        <div class="logo">
          <img src="@/assets/imgs/tripleUniB.svg" alt="logo" />
        </div>
      </div>
      <div class="page b">
        <div class="text">
          <p class="title">问些问题</p>
          <p class="desc">
            不知道怎么选课？<br />
            不知道学校附近吃什么？<br /><br />
            无论什么问题，热心大学生来帮你！
          </p>
        </div>
        <div class="img">
          <p class="seen">分享</p>
          <p class="new">咨询</p>

          <div class="img-background-wrapper">
            <div class="img-background"></div>
          </div>
          <img
            class="content"
            src="https://picsum.photos/id/28/200/300"
            alt="function display"
          />
          <img
            class="frame"
            src="@/assets/imgs/iphone15.webp"
            alt="phone frame"
          />
        </div>
        <div class="logo">
          <img src="@/assets/imgs/tripleUniB.svg" alt="logo" />
        </div>
      </div>
      <div class="page c">
        <div class="text">
          <p class="title">到处看看</p>
          <p class="desc">
            浏览树洞，<br />
            邂逅惊喜！
          </p>
        </div>
        <div class="img">
          <p class="seen">分享</p>
          <p class="seen">咨询</p>
          <p class="new">放松</p>

          <div class="img-background-wrapper">
            <div class="img-background"></div>
          </div>
          <img
            class="content"
            src="https://picsum.photos/id/29/200/300"
            alt="function display"
          />
          <img
            class="frame"
            src="@/assets/imgs/iphone15.webp"
            alt="phone frame"
          />
        </div>
        <div class="logo">
          <img src="@/assets/imgs/tripleUniB.svg" alt="logo" />
        </div>
      </div>
      <div class="page d">
        <div class="text">
          <p class="title">聊聊天吧</p>
          <p class="desc">
            匿名向任何人发送消息，<br />
            寻找属于你们的共鸣。
          </p>
        </div>
        <div class="img">
          <p class="seen">分享</p>
          <p class="seen">咨询</p>
          <p class="seen">放松</p>
          <p class="new">交友</p>

          <div class="img-background-wrapper">
            <div class="img-background"></div>
          </div>
          <img
            class="content"
            src="https://picsum.photos/id/30/200/300"
            alt="function display"
          />
          <img
            class="frame"
            src="@/assets/imgs/iphone15.webp"
            alt="phone frame"
          />
        </div>
        <div class="logo">
          <img src="@/assets/imgs/tripleUniB.svg" alt="logo" />
        </div>
      </div>
      <div class="page e">
        <div class="text">
          <p class="title">好东西,<br />存了</p>
          <p class="desc">有趣的树洞不容错过，<br />收藏下来，随时回顾。</p>
        </div>
        <div class="img">
          <p class="seen">分享</p>
          <p class="seen">咨询</p>
          <p class="seen">放松</p>
          <p class="seen">交友</p>
          <p class="new">都在这里!</p>

          <div class="img-background-wrapper">
            <div class="img-background"></div>
          </div>
          <img
            class="content"
            src="https://picsum.photos/id/32/200/300"
            alt="function display"
          />
          <img
            class="frame"
            src="@/assets/imgs/iphone15.webp"
            alt="phone frame"
          />
        </div>
        <div class="logo">
          <img src="@/assets/imgs/tripleUniB.svg" alt="logo" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, computed, defineProps } from "vue";

const props = defineProps({});

let isMobile = computed(() => {
  return false;
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

function clipPath(startingOffset, numberOfPages) {
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
    if (window.innerWidth < 700) {
      page.style.clipPath = `inset(0 0 0 ${
        ((window.scrollY - startingOffset - i * window.innerHeight) /
          window.innerHeight) *
        -100
      }%)`;
      continue;
    }
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
  margin-top: 5rem;
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
  --_clr: #ce50b5;
  display: grid;
  grid-template-columns: 1.618fr 1fr;
  transition: clip-path 0.05s linear;
  background-color: color-mix(in lab, var(--_clr) 3%, white 97%);
}
.page:not(:first-child) {
  clip-path: inset(100% 0 0 0);
}

.text {
  padding: 17svh 5vw;
}

.title {
  font-size: clamp(4rem, 8vw, 7rem);
  font-weight: 900;
}

.desc {
  margin-top: 3rem;
  padding-inline: 2rem clamp(0px, 30%, 150px);
  font-size: 2em;
  font-weight: bold;
  max-width: 30ch;
}

.img {
  position: relative;
  background-color: var(--_clr);
  width: 100%;
  height: 100%;
  padding: 3rem;
}

.content {
  padding: 2%;
  border-radius: 44px;
}

.img img,
.img-background-wrapper {
  position: absolute;
  top: 50%;
  left: 0%;
  transform: translate(-60%, -45%) rotate(10deg);
  aspect-ratio: 73 / 149;
  height: 70%;
}
.img-background-wrapper {
  display: grid;
  place-items: center;
}

.img-background {
  width: 96%;
  height: 97%;
  border-radius: 44px;
  background-color: rgb(211, 211, 211);
}

.img p {
  font-size: 3em;
  color: white;
  font-weight: bold;
  text-align: right;
  margin: 1rem;
}

.logo {
  position: absolute;
  bottom: 2rem;
  left: 2rem;
  width: 10vw;
}

.img .seen {
  color: color-mix(in lab, var(--_clr) 30%, black 70%);
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
  --_clr: rgb(206, 211, 105);
}
.e {
  --_clr: #dd80c8;
}

@media screen and (max-width: 700px) {
  .scroll-wrapper {
    margin-top: 0;
  }
  .page {
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1.2fr;
  }

  .text {
    padding: 3rem 1rem;
  }

  .desc {
    margin-top: 0.5rem;
    padding-inline: 1rem;
    font-size: var(--fs-700);
    max-width: unset;
    text-align: right;
  }

  .img img,
  .img-background-wrapper {
    position: absolute;
    top: 40%;
    left: 5%;
    transform: translate(0, -50%);
    aspect-ratio: 73 / 149;
    height: unset;
    width: 55%;
  }
  .img-background,
  .content {
    border-radius: 2rem;
  }

  .img {
    padding: 3rem 1rem;
  }

  .img p {
    font-size: var(--fs-800);
    margin: 1rem 0.5rem;
  }
  .logo {
    left: unset;
    right: 1rem;
    width: 4rem;
  }
}
</style>
