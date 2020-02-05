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

      let imgElement = document.getElementById('img');
      imgElement.onload = function(){
      let src = cv.imread('img')
      let dst = new cv.Mat();
      /*let colorSpaces = [
        cv.COLOR_RGB2BGRA,
        cv.COLOR_RGBA2GRAY,
        cv.COLOR_RGBA2BGR565,
        cv.COLOR_RGBA2mRGBA,
        cv.COLOR_RGBA2YUV_I420,
        cv.COLOR_RGBA2YUV_YV12
      ]*/

      cv.cvtColor(src, dst, cv.COLOR_RGB2BGRA);
      //cv.Set(src, )
      cv.imshow('canvas', dst);
      //src.delete(); dst.delete();
      cv.cvtColor(src, dst, cv.COLOR_RGBA2GRAY);
      cv.imshow('canvas', dst);
      }
    }
}
</script>

<style>
.tomato{
  width: auto;
  height: 45vh;
}
</style>