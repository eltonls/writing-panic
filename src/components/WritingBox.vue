<script> 
  export default {
    data() {
      return {
          wordCount: 0,
          setTimerId: null
      } 
    },
    props: ["isGameOn"],
    methods: {
      startCDTimer: function() {
        this.setTimerId = setTimeout(() => {
          console.log("Começa timer:" + this.setTimerId);
          this.$emit("starTimer");
        }, 4000)
      },

      breakCDTimer: function() {
        if(this.setTimerId !== null) {
          console.log("Quebra timer: " + this.setTimerId)
          clearTimeout(this.setTimerId);
        }
      },

      countWords: function(evt) {
        const array = evt.target.value.trim().split(" ");

        if(array[0] === "") {
          this.wordCount = 0;
          return 0;
        }

        this.wordCount = array.length; 
      }
    },
  }  
</script>

<template>
  <div class="writing-box">
    <textarea @keydown="breakCDTimer" @keyup="startCDTimer"  ></textarea> 
    <p class="writing-box__words">{{wordCount}}</p>
  </div>
</template>

<style scoped>
  .writing-box {
    @apply w-3/6 h-full;
    @apply bg-opacity-25;
    @apply rounded-md overflow-hidden;
  } 

  .writing-box__words {
    @apply p-2;
    @apply fixed top-1 left-1;
    @apply text-3xl text-white;
    @apply bg-black bg-opacity-50;
    @apply rounded-md;
  }

  textarea {
      @apply resize-none;
      @apply w-full h-full;
      @apply bg-black;
      @apply bg-opacity-50;
      @apply text-white font-serif;
      @apply p-2;
  }
</style>
