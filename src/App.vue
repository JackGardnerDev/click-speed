<script setup>

  import { ref } from 'vue'

  const count = ref(0)
  const seconds = ref(10);
  const isButtonDisabled = ref(false)
  let countdownInterval

  const handleClick = () => {
    if (!isButtonDisabled.value) {
      count.value++
      
      if (!countdownInterval) {
        startCountdown()
      }
    }
  }

  // Function to start the countdown
  const startCountdown = () => {
    countdownInterval = setInterval(() => {
      seconds.value--

      if (seconds.value === 0) {
        clearInterval(countdownInterval)
        isButtonDisabled.value = true
      }
    }, 1000)
  }

</script>

<template>

  <div id="app">
    <button class="button" @click="handleClick" :disabled="isButtonDisabled">Click Here</button>
    <div class="counters">
      <div class="click-count">Click Count: {{ count }}</div>
      <div class="seconds-count">Seconds: {{ seconds }}</div>
    </div>
    
  </div>

</template>

<style scoped>

</style>