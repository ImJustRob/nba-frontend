<script>
export default {
  props: {
    player: Object,
  },
};
</script>

<template>
  <div>
    <h1>Player information</h1>
    <p>Team: {{ player.team }}</p>
    <p>Image: {{ player.image }}</p>
    <p>Points Average: {{ player.points_avg }}</p>
    <p>Player: {{ player.player }}</p>
  </div>
</template>

<style></style>