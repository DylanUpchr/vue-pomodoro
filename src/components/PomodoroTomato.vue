<template>
  <div>
    <img class="tomato" alt="Tomato" src="../assets/tomato.jpg">
  </div>
</template>

<script>
export default {
    name: 'PomodoroTomato',
}
</script>

<style>

.tomato{
  width: auto;
  height: 45vh;
 /* animation: grayInLoad 2s infinite;*/
 /* -webkit-animation-direction: alternate-reverse;*/
}
/*@-webkit-keyframes grayInLoad {
  from {
    filter: grayscale(0%);
  }
  to {
    filter: grayscale(100%);
  }
}
@keyframes grayInLoad {
  from {
    filter: grayscale(0%);
  }
  to {
    filter: grayscale(100%);
  }
}*/
</style>