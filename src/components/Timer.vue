<script>
export default {
  data() {
    return {
      timer: 20,
      timerInterval: null,
    }
  },
  props: ["isWriting"],
  methods: {
    toggleTimer: function() {
      if(this.isWriting === false) {
        this.timerInterval = setInterval(() => {
          this.timer -= 1; 
        }, 1000);
      } else {
        this.timer = 20;
      }
    }
  },
}
</script>

<template>
  <div class="timer">
    Tempo: {{ this.timer.toLocaleString("pt-br", {minimumIntegerDigits: 2}) }}s       
  </div>
</template>

<style scoped>
  .timer {
    @apply p-2;
    @apply fixed top-1 right-1;
    @apply text-3xl text-white;
    @apply bg-black bg-opacity-50;
    @apply rounded-md;
  } 
</style>
