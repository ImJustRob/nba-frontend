<script>
export default {
  props: {
    player: Object,
  },
  data: function () {
     return {
       editPlayerParams: {},
     };
   },
   created: function () {
     this.editPlayerParams = { ...this.player };
   },
   methods: {
     handleSubmit: function () {
       this.$emit("updatePlayer", this.player.id, this.editPlayerParams);
     },
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
    <form v-on:submit.prevent="handleSubmit">
       <div>
         Team:
         <input v-model="editPlayerParams.team" type="text" />
       </div>
       <div>
         Image:
         <input v-model="editPlayerParams.image" type="text" />
       </div>
       <div>
         Points Average:
         <input v-model="editPlayerParams.points_avg" type="text" />
       </div>
       <div>
         Player:
         <input v-model="editPlayerParams.player" type="text" />
       </div>
       <button type="submit">Update Player</button>
     </form>
  </div>
</template>

<style></style>