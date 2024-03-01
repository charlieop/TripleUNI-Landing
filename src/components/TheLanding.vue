<template>
  <a class="logo" href="">
    <img src="@/assets/imgs/U.png" alt="logo" />
  </a>
  <div class="wrapper">
    <div class="slogan">
      <h1>
        <img
          src="@/assets/imgs/tripleUniW.png"
          alt="Triple Uni"
          width="512"
          height="122"
        />
      </h1>
      <h2>港三专属的树洞平台</h2>
    </div>
    <div class="login">
      <a
        href="https://tripleuni.com/login?callback=%2Fhome"
        class="button strong"
        >立即登陆</a
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
  </div>
</template>

<script setup>
import { ref, defineProps } from "vue";

const props = defineProps({});
</script>

<style scoped>
.logo {
  position: absolute;
  top: 0.75rem;
  left: 1rem;
  width: 4rem;
  aspect-ratio: 1 / 1;
}

.wrapper {
  --_landing-padding: 10vh;
  --_landing-padding: 10svh;
  height: calc(100vh - var(--_landing-padding));
  height: calc(100svh - var(--_landing-padding));
  padding-top: var(--_landing-padding);
  padding-inline: 12vw;

  display: grid;
  grid-template-columns: 1fr 1fr;
  place-items: center;
}

@media screen and (max-width: 700px) {
  .wrapper {
    grid-template-columns: 1fr;
    gap: 0;
    --_landing-padding: 13vh;
    --_landing-padding: 13svh;
  }
}

h2 {
  margin-top: 2rem;
  font-size: var(--fs-700);
  font-weight: 900;
  color: white;
  text-align: right;
}

.login {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
  width: 100%;
}

.button {
  position: relative;
  padding: 0.75rem 1.25rem;
  width: min(80%, 22rem);
  min-width: fit-content;
  border-radius: 100rem;
  background-color: white;
  box-shadow: 0 0.2rem 1rem rgba(0, 0, 0, 0.1);

  color: var(--color-primary);
  font-size: var(--fs-500);
  text-align: center;
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
  background-color: #119be5;
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
</style>
