<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { ref, onMounted } from 'vue'

// [Effect 1] Live Clock
const time = ref(new Date().toLocaleTimeString())
setInterval(() => { time.value = new Date().toLocaleTimeString() }, 1000)

// [Effect 2] Random Color Box
const color = ref('#'+Math.floor(Math.random()*16777215).toString(16))
function changeColor() {
  color.value = '#'+Math.floor(Math.random()*16777215).toString(16)
}

// [Effect 3] Counter Button
const count = ref(0)
function increment() { count.value++ }

// [Effect 4] Typewriter Effect
const fullText = 'Welcome to Vue with Effects!'
const typewriter = ref('')
let idx = 0
function typeEffect() {
  if (idx < fullText.length) {
    typewriter.value += fullText[idx++]
    setTimeout(typeEffect, 100)
  }
}
onMounted(typeEffect)

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

//todo update style
