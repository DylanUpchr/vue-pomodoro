<template>
  <div>
    <button v-onclick='IsClicked' :disabled='clicked'>Play</button>
    <button >Pause</button>
    <button >Stop</button>
  </div>
</template>

<script>
export default {
    name: 'PomodoroButton',
    methods: {
        IsClicked() {
        }
    }
}
</script>

<style>

</style>