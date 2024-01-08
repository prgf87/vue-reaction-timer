<template lang="eng">
  <div>
    <p>
        Reaction Time: {{score}}ms
    </p>
    <p class="rank">
        {{rank}}
    </p>
    </div>
</template>
<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Phwoooarrr! You are Super Speedy!!";
    } else if (this.score < 400) {
      this.rank = "Nice Nimble Fingers";
    } else {
      this.rank = "Snail's Pace";
    }
  },
};
</script>
<style>
.rank {
  color: #0faf87;
  font-size: 24px;
}
</style>
