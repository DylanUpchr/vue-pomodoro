<template>
  <div>
    <PomodoroTitle></PomodoroTitle>
    <PomodoroTomato></PomodoroTomato>
    <PomodoroButton></PomodoroButton>
    <PomodoroTimer></PomodoroTimer>
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
  }
}
</script>

<style>

</style>