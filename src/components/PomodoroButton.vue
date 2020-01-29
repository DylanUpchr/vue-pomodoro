<template>
  <div>
      <!--Pomodoro controls-->
    <button ref="playButton" v-on:click="IsClicked('playButton')"><font-awesome-icon icon="play"/></button>
    <button ref="pauseButton"  v-on:click="IsClicked('pauseButton')"><font-awesome-icon icon="pause"/></button>
    <button ref="stopButton"  v-on:click="IsClicked('stopButton')"><font-awesome-icon icon="stop"/></button>
  </div>
</template>

<script>
export default {
    name: 'PomodoroButton',
    methods: {
        //Change button states according to which one was clicked and emit the proper event
        IsClicked(item) {
            switch(item) {
                default:
                case "playButton":
                    this.$refs[item].disabled = true;
                    this.$refs["pauseButton"].disabled = false;
                    this.$refs["stopButton"].disabled = false;
                    this.$emit("play");
                    break;
                case "pauseButton":
                    this.$refs["playButton"].disabled = false;
                    this.$refs[item].disabled = true;
                    this.$refs["stopButton"].disabled = false;
                    this.$emit("pause");
                    break;
                case "stopButton":
                    this.$refs["playButton"].disabled = false;
                    this.$refs["pauseButton"].disabled = false;
                    this.$refs[item].disabled = true;
                    this.$emit("stop");
                    break;
            }
        },
        //Reset buttons reset event is emitted from PomodoroTimer
        Reset() {
            this.$refs["playButton"].disabled = true;
            this.$refs["pauseButton"].disabled = false;
            this.$refs["stopButton"].disabled = false;
        }
    },
    created(){
      this.$parent.$on('reset', this.Reset);
    }
}
</script>

<style>

</style>