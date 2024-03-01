<template>
  <div class="wrapper">
    <h1>Hello World</h1>
    <h2>{{ msg }}</h2>
    <button @click="count++">count is: {{ count }}</button>
  </div>
</template>

<script setup>
import { ref, defineProps } from "vue";

const props = defineProps({
  msg: String,
});

const count = ref(0);
</script>
<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
  padding-top: 6rem;
}

h1 {
  font-size: var(--fs-900);
  font-family: var(--ff-accent);
}

h2 {
  font-size: var(--fs-500);
  color: var(--clr-text-muted);
}

button {
  margin-top: 3rem;
  padding: 1rem 2rem;
  line-height: 1.2;
  font-size: var(--fs-500);
  background-color: var(--clr-background-muted);
  border: 3px solid var(--clr-primary);
  border-radius: 0.5rem;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
}

button:hover {
  background-color: var(--clr-primary);
  color: var(--clr-background);
  border-color: var(--clr-text);
}
</style>
