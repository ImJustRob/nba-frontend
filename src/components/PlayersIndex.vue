<script>
export default {
   props: {
     players: Array,
   },
 };
</script>

<template>
  <div>
    <h1>All Players</h1>
    <div v-for="player in players" v-bind:key="player.id">
       <h2>{{ player.team }}</h2>
       <img v-bind:src="player.image" />
       <p>Points Average: {{ player.points_avg }}</p>
       <p>Player: {{ player.player }}</p>
     </div>
  </div>
</template>

<style></style>