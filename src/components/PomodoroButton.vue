<template>
  <div>
    <button ref="playButton" v-on:click="IsClicked('playButton')"><font-awesome-icon icon="play"/></button>
    <button ref="pauseButton"  v-on:click="IsClicked('pauseButton')"><font-awesome-icon icon="pause"/></button>
    <button ref="stopButton"  v-on:click="IsClicked('stopButton')"><font-awesome-icon icon="stop"/></button>
  </div>
</template>

<script>
export default {
    name: 'PomodoroButton',
    methods: {
        IsClicked(item) {
            switch(item) {
                default:
                case "playButton":
                    this.$refs[item].disabled = true;
                    this.$refs["pauseButton"].disabled = false;
                    this.$refs["stopButton"].disabled = false;
                    break;
                case "pauseButton":
                    this.$refs["playButton"].disabled = false;
                    this.$refs[item].disabled = true;
                    this.$refs["stopButton"].disabled = false;
                    break;
                case "stopButton":
                    this.$refs["playButton"].disabled = false;
                    this.$refs["pauseButton"].disabled = false;
                    this.$refs[item].disabled = true;
                    break;
            }
        }
    }
}
</script>

<style>

</style>