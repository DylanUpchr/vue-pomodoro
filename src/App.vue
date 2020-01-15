<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <pomodoro></pomodoro>
    <cat-a-p-i></cat-a-p-i>
  </div>
</template>

<script>
import Pomodoro from './components/Pomodoro.vue'
import CatAPI from './components/CatAPI.vue'

export default {
  name: 'app',
  components: {
    Pomodoro,
    CatAPI
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
