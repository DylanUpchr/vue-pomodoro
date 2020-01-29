<template>
  <div>
      <label ref="clock"></label><br/>
      <label>{{ this.WorkingState ? "WORK!" : "REST!" }}</label>
  </div>
</template>

<script>
export default {
    name: 'PomodoroTimer',
    data(){
      return {
        WorkingState: false,
        Active: this.timerState,
        Time: 1200,
        Minutes: 0,
        Seconds: -1
      }
    },
    methods: {
      'play': function(){
          this.Active = true
          if(this.Seconds == -1){
            this.work()
          }
      },
      'pause': function(){
          this.Active = false
      },
      'work': function() {
        this.Minutes = 25
        this.Seconds = 0
        this.WorkingState = true
      },
      'rest': function(){
        this.Minutes = 5
        this.Seconds = 0
        this.WorkingState = false
      },
      'reset': function(){
        this.Minutes = 25
        this.Seconds = 0
        this.$emit('reset')
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
            if(this.WorkingState){
              this.rest()
            }else{
              this.work()
            }
          }
          this.$refs.clock.innerHTML = this.Minutes + ":" + (this.Seconds > 9 ? this.Seconds : "0" + this.Seconds)
        }
      }
    },
    props: {
      timerState: Boolean,
    },
    created(){
      this.$parent.$on('play', this.play)
      this.$parent.$on('pause', this.pause)
      this.$parent.$on('stop', this.reset)
      this.timer = setInterval(this.tick, 1000)
    }
}
</script>

<style>

</style>