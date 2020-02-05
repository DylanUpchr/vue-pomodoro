<template>
  <div>
    <img hidden id="img" class="tomato" alt="Tomato" src="../assets/tomato.jpg">
    <canvas id="canvas" width="400" height="400"></canvas>
  </div>
</template>

<script>
import * as cv from 'opencv.js'
export default {
    name: 'PomodoroTomato',
    mounted(){

      let imgElement = document.getElementById('img')
      imgElement.onload = function(){
      let src = cv.imread('img')
      let dst = new cv.Mat()
      let dsize = new cv.Size(src.rows, src.cols);
      let center = new cv.Point(src.cols / 2, src.rows / 2);
      let colorSpaces = [
        cv.COLOR_RGB2BGRA,
        cv.COLOR_RGBA2GRAY,
        cv.COLOR_RGBA2BGR565
      ]

      setInterval(function(){
        // You can try more different parameters
        cv.cvtColor(src, dst, colorSpaces[Math.floor(Math.random() * 3)])
        let M = cv.getRotationMatrix2D(center, Math.floor(Math.random() * 180), 1);
        cv.warpAffine(dst, dst, M, dsize, cv.INTER_LINEAR, cv.BORDER_CONSTANT, new cv.Scalar());
        cv.imshow('canvas', dst)
      },
      300000)
      }
    }
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