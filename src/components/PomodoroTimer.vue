<template>
  <div>
      <label ref="clock"></label><br/>
      <label>{{ this.Active ? "WORK!" : "REST!" }}</label>
  </div>
</template>

<script>
export default {
    name: 'PomodoroTimer',
    data(){
      return {
        Active: this.timerState,
        Time: 1200,
        Minutes: 0,
        Seconds: 20
      }
    },
    methods: {
      'changeState': function(){
        this.Active = !this.Active
      },
      'reset': function(){
        this.changeState()
        this.Minutes = 0
        this.Seconds = 20
      },
      'tick': function(){
        if(this.Active){
          if(this.Seconds == 0 && this.Seconds != null){
            this.Minutes--
            this.Seconds = 60
          }else{
            this.Seconds--
          }
          if (this.Minutes == 0 && this.Seconds == 0){
            this.reset()
          }
          this.$refs.clock.innerHTML = this.Minutes + ":" + this.Seconds
        }
      }
    },
    props: {
      timerState: Boolean
    },
    created(){
      this.$parent.$on('play', this.changeState)
      this.$parent.$on('pause', this.changeState)
      this.$parent.$on('stop', this.reset)
      this.timer = setInterval(this.tick, 1000)
    }
}
</script>

<style>

</style>