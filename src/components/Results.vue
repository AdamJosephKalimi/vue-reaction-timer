<template>
    <div>
        <p>Reaction Time: {{ reactionTime }} MS</p>
        <p class="rank">{{ rank }} </p>
    </div>
</template>

<script>
export default {
  props: ["reactionTime"],
  data() {
    return {
      rank: null
    };
  },
  mounted() {
    if (this.reactionTime < 250) {
      this.rank = "Jedi Reflexes - This is the way";
    } else if (this.reactionTime >= 250 && this.reactionTime <= 600) {
      this.rank = "Apprentice Reflexes - Soon, but not yet";
    } else {
      this.rank = "Padawan Reflexes - Still much to learn";
    }
  },
  methods: {}
};
</script>

<style>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
