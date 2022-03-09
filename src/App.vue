<template>
  <h1>Reaction Timer Game</h1>
  <button @click="startTimer" :disabled="isPlaying">Play</button>
  <p v-if="userReactionScore && !isPlaying">
    Reaction time : {{ userReactionScore }}ms
  </p>
  <Block v-if="isPlaying" :delay="delay" @userTime="userReactionTime" />
</template>

<script>
import Block from "./components/Block.vue";

export default {
  name: "App",
  components: { Block },
  data() {
    return {
      isPlaying: false,
      delay: null,
      userReactionScore: null,
    };
  },
  methods: {
    startTimer() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      console.log(this.delay);
    },
    userReactionTime(reactionTime) {
      this.userReactionScore = reactionTime;
      this.isPlaying = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
