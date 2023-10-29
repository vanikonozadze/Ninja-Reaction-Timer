<template>
  <p>Reaction time: {{ score }} ms</p>
  <p class="rank">Ranking: {{ rankName }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rankName: null,
    };
  },
  mounted() {
    if (this.score <= 250) {
      this.rankName = "NINJA";
    } else if (this.score <= 350) {
      this.rankName = "HALF-NINJA";
    } else {
      this.rankName = "TURTLE";
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
