<template>
  <p>Reaction time: {{ score }} ms</p>
  <p class="rank">Ranking: {{ rankName }}</p>
  <p v-if="highScoreBlock">High Score: {{ highScore }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rankName: null,
      highScoreBlock: true,
    };
  },
  computed: {
    highScore() {
      // Get the high score from localStorage
      return localStorage.getItem("highScore") || 0;
    },
  },
  mounted() {
    if (this.score <= 250) {
      this.rankName = "NINJA";
    } else if (this.score <= 350) {
      this.rankName = "HALF-NINJA";
    } else {
      this.rankName = "TURTLE";
    }

    if (this.score < this.highScore) {
      // Update the high score in localStorage
      localStorage.setItem("highScore", this.score);
    }
  },
};
</script>

<style>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
