<script>
import WritingBox from "./components/WritingBox.vue"
import Timer from "./components/Timer.vue"

export default {
  components: {WritingBox, Timer},

  data() {
    return {
      isWriting: true, // always true, even before game starts
    }
  },
  methods: {
    startTimer: function() {
      if(this.isWriting) {
        this.isWriting = false;
      }
    }
  }, 
}
</script>

<template>
  <div class="body">
    <Timer isWriting="isWriting" />
    <WritingBox @startTimer="startTimer" />
  </div>
</template>

<style scoped>
  .body {
      @apply h-screen;
      @apply p-2;
      @apply flex flex-row justify-center items-center;
  }
</style>
