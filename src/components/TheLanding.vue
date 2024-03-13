<template>
  <section class="landing-section">
    <div class="wrapper">
      <div class="content">
        <a class="logo" href="">
          <img src="@/assets/imgs/U.png" alt="logo" />
        </a>
        <h1>
          <img
            src="@/assets/imgs/tripleUniB.svg"
            alt="Triple Uni"
            width="512"
            height="122"
          />
        </h1>
        <h2>
          <span>港</span><span>三</span><span>专</span><span>属</span
          ><span>的</span><span>树</span><span>洞</span><span>平</span
          ><span>台</span>
        </h2>
        <a
          href="https://tripleuni.com/login?callback=%2Fhome"
          class="button strong"
          >立即登入</a
        >
        <div class="button">
          使用小程序版
          <div class="hover">
            <img
              src="@/assets/imgs/applet-code.jpg"
              alt="wechat"
              width="100"
              height="100"
            />
          </div>
        </div>
      </div>
      <div class="decoration">
        <div class="frame frame3"></div>
        <div class="frame frame2"></div>
        <div class="frame frame1"></div>
        <div class="ball ball1">
          <img
            src="@/assets/imgs/red_button.svg"
            alt=""
            width="111"
            height="111"
          />
        </div>
        <div class="ball ball2">
          <img
            src="@/assets/imgs/green_button.svg"
            alt=""
            width="111"
            height="111"
          />
        </div>
        <div class="ball ball3">
          <img
            src="@/assets/imgs/purple_button.svg"
            alt=""
            width="111"
            height="111"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, defineProps } from "vue";

const props = defineProps({});
</script>

<style scoped>
.logo {
  position: absolute;
  top: -10rem;
  left: 0;
  width: 5rem;
  aspect-ratio: 1 / 1;
}

.landing-section {
  --_landing-padding: 10svh;
  height: calc(100svh - var(--_landing-padding));
  padding-top: var(--_landing-padding);
  padding-inline: 8vw;
  display: grid;
  place-items: center;
}

.wrapper {
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 5vw;
  align-items: center;
}

.decoration {
  position: relative;
  width: 100%;
  height: max(100%, 50svh);
}
.decoration::before {
  content: "";
  position: absolute;
  top: -30%;
  left: -15%;
  width: 130%;
  height: 150%;
  background-repeat: no-repeat;
  background-blend-mode: lighten;
  background-size: 100% 100%;
  background-position: 0px 0px, 0px 0px, 0px 0px;
  background-image: radial-gradient(
      32% 50% at 65% 49%,
      #67abb888 13%,
      #00000000 100%
    ),
    radial-gradient(32% 33% at 38% 64%, #8761d188 20%, #00000000 100%),
    radial-gradient(33% 26% at 38% 30%, #e8585888 19%, #00000000 96%);
  animation: background-movement 10s infinite linear;
}

@keyframes background-movement {
  0% {
    background-position: 0px 0px, 0px 0px, 0px 0px;
    transform: rotate(-7deg);
  }
  25% {
    background-position: 0px -12px, 20px -15px, -15px 10px;
  }
  50% {
    transform: scale(1.05);
    background-position: 7px 0px, 0px 0px, -1.5cm 0cm;
  }
  75% {
    background-position: 0px 12px, -20px 15px, -15px -10px;
  }
  100% {
    background-position: 0px 0px, 0px 0px, 0px 0px;
    filter: brightness(0.9);
    transform: rotate(-7deg);
  }
}

.frame {
  position: absolute;
  width: min(20rem, 25vw);
  top: 45%;
  left: 5%;
  aspect-ratio: 16 / 10;
  background-color: rgba(255, 255, 255, 0.337);
  border-radius: min(2.875rem, 3.5vw);
  border: 1.5px solid #ffffff6e;
  box-shadow: 0 0.2rem 0.75rem rgba(255, 255, 255, 0.294);
  transition: all 0.3s ease-in-out;

  backdrop-filter: blur(6px);
  -webkit-backdrop-filter: blur(6px);
}

.frame:hover {
  width: min(20.1rem, 25.1vw);
  box-shadow: 0 0.5rem 1rem rgba(255, 255, 255, 0.548);
  filter: brightness(1.05);
}

.ball {
  --_color: black;
  position: absolute;
  color: white;
  width: min(7rem, 9vw);
  aspect-ratio: 1 / 1;
  border-radius: 1000rem;
  transition: all 0.3s ease-in-out;
}

.ball:hover {
  transform: translateY(-3%);
  filter: contrast(1.3);
}

.frame1 {
  transform: translateY(-50%);
}
.frame2 {
  transform: translateY(-50%) translate(40%, -65%);
}
.frame3 {
  transform: translateY(-50%) translate(65%, 55%);
}

.ball1 {
  top: 2%;
  left: 13%;
}
.ball2 {
  top: 29%;
  right: 10%;
}
.ball3 {
  bottom: 15%;
  left: 25%;
}

.content {
  position: relative;
  z-index: 1;
}

h1 img {
  width: 100%;
}

h2 {
  padding-inline: 1rem;
  margin-block: 2rem;
  display: flex;
  justify-content: space-between;
  font-size: var(--fs-700);
  font-weight: 700;
}

.button {
  position: relative;
  padding: 0.75rem 1.25rem;
  display: block;
  margin: 1.25rem 2.5rem;
  border-radius: 100rem;
  background-color: white;
  box-shadow: 0 0.2rem 1rem rgba(0, 0, 0, 0.1);
  border: 3px solid black;

  color: var(--color-primary);
  font-size: var(--fs-500);
  text-align: center;
  letter-spacing: 0.75ch;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
}
.button:hover {
  text-decoration: none;
  transform: scale(1.02) translateY(-0.1rem);
  box-shadow: 0 0.5rem 1rem rgba(0, 0, 0, 0.15);
  filter: brightness(1.05);
}

.strong {
  background-color: black;
  color: white;
  font-weight: 700;
}

.hover {
  position: absolute;
  top: 100%;
  left: 50%;
  transform: translate(-50%, 0);
  width: clamp(9rem, 80%, 12rem);
  aspect-ratio: 1 / 1;
  box-shadow: 0 0.2rem 1rem rgba(0, 0, 0, 0.1);
  opacity: 0;
  pointer-events: none;
  transition: all 0.3s ease-in-out;
  border-radius: 1rem;
  background-color: #ffffff32;
}

.hover img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 1rem;
}

.button:hover .hover {
  opacity: 1;
  top: calc(120% + 0.5rem);
  transform: translate(-50%, -0.5rem);
  pointer-events: all;
}

@media screen and (max-width: 1200px) {
  .landing-section {
    padding-inline: 3vw;
  }
  .wrapper {
    gap: 3vw;
  }
}

@media screen and (max-width: 700px) {
  .landing-section {
    padding-top: 5rem;
  }
  .logo {
    top: -3rem;
    left: 50%;
    width: 3.5rem;
    transform: translate(-50%, -50%);
    aspect-ratio: 1 / 1;
  }
  .wrapper {
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr;
    gap: 7rem;
    place-items: center;
    overflow-x: clip;
  }

  .decoration {
    width: 85%;
    height: 100%;
  }

  .frame {
    width: max(9rem, 32.5vw);
    left: calc(55% - max(9rem, 32.5vw));
  }
  .frame:hover {
    width: max(9.01rem, 32.51vw);
  }
  .ball {
    width: max(4rem, 13vw);
  }

  .content {
    padding-inline: 3rem;
  }

  h1 {
    padding-inline: 3rem;
  }

  h2 {
    font-size: var(--fs-600);
    margin-block: 0.75rem;
    padding-inline: 2rem;
  }
  .button {
    margin: 1.25rem 5.75rem;
    font-size: var(--fs-400);
  }
  .button:not(.strong) {
    background-color: transparent;
  }
}
</style>
