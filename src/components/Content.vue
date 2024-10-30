<script>
import axios from "axios";
import PlayersIndex from "./PlayersIndex.vue";

export default {
  components: {
    PlayersIndex,
  },
   data: function () {
     return {
       players: [],
     };
   },
   created: function () {
     this.handleIndexPlayers();
   },
   methods: {
     handleIndexPlayers: function () {
       axios.get("http://localhost:3000/nbas.json").then((response) => {
         console.log("players index", response);
         this.players = response.data;
       });
     },
   },
};
</script>

<template>
  <main>
     <PlayersIndex v-bind:players="players" />
  </main>
</template>

<style></style>
