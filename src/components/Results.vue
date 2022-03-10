<template>
  <p>Reaction time : {{ userReactionScore }}ms</p>
  <p class="rankClass">{{ rank }}</p>
</template>

<script>
export default {
  props: ["userReactionScore"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.userReactionScore < 250) {
      this.rank = "Ninja Fingers";
    } else if (this.userReactionScore < 400) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = "Snail Pace...";
    }
  },
};
</script>

<style>
.rankClass {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>