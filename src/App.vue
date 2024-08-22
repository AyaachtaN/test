<script setup>
// import HelloWorld from './components/HelloWorld.vue'
import FirstTest from './components/FirstTest.vue';
import SecondTest from './components/SecondTest.vue';
</script>

<template>
  <div class="text-element">Test 1</div>
  <FirstTest/>
  <div class="text-element">Test 2</div>
  <SecondTest/>
 
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
.text-element {
  font-size: 30px;
  color: black;
  text-align: left;
  padding: 5% 0 5% 0%;
}
</style>
