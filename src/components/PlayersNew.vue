<script>
export default {
   data: function () {
     return {
       newPlayerParams: {},
     };
   },
   methods: {
     handleSubmit: function () {
       this.$emit("createPlayer", this.newPlayerParams);
       this.newPlayerParams = {};
     },
   },
 };
</script>

<template>
  <div>
    <h1>New Player</h1>
    <form v-on:submit.prevent="handleSubmit">
      <div>
        Team:
        <input name="team" type="text" v-model="newPlayerParams.team" />
      </div>
      <div>
        Image:
        <input name="image" type="text" v-model="newPlayerParams.image" />
      </div>
      <div>
        Player:
        <input name="player" type="text" v-model="newPlayerParams.player" />
      </div>
      <div>
        Points Average:
        <input name="points_avg" type="text" v-model="newPlayerParams.points_avg" />
      </div>
      <button type="submit">Create Player</button>
    </form>
  </div>
</template>

<style></style>