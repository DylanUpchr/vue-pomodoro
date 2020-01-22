<template>
  <div>
    <PomodoroTitle></PomodoroTitle>
    <PomodoroTomato></PomodoroTomato>
    <PomodoroButton v-on:play="ReEmitPlay" v-on:pause="ReEmitPause" v-on:stop="ReEmitStop"></PomodoroButton>
    <PomodoroTimer :timerState="this.TimerState"></PomodoroTimer>
  </div>
  
</template>

<script>
import PomodoroTitle from './PomodoroTitle'
import PomodoroTomato from './PomodoroTomato'
import PomodoroButton from './PomodoroButton'
import PomodoroTimer from './PomodoroTimer'
 
export default {
  name: 'Pomodoro',
  components: {
    PomodoroTitle,
    PomodoroTomato,
    PomodoroButton,
    PomodoroTimer,
  },
  methods: {
    ReEmitPlay() {
      this.$emit("play");
    },
    ReEmitPause() {
      this.$emit("pause");
    },
    ReEmitStop() {
      this.$emit("stop");
    },
  },
  data(){
    return{
      TimerState: false
    }
  }
}
</script>

<style>

</style>