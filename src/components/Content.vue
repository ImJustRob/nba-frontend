<script>
import axios from "axios";
import PlayersIndex from "./PlayersIndex.vue";
import PlayersNew from "./PlayersNew.vue";
import PlayersShow from "./PlayersShow.vue";
import Modal from "./Modal.vue";
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';

export default {
  components: {
    PlayersIndex,
    PlayersNew,
    PlayersShow,
    Modal,
  },
   data: function () {
     return {
       players: [],
       currentPlayer: {},
       isPlayersShowVisible: false,
     };
   },
   created: function () {
     this.handleIndexPlayers();
   },
   methods: {
     handleIndexPlayers: function () {
       axios.get("http://localhost:5000/nbas.json").then((response) => {
         console.log("players index", response);
         this.players = response.data;
       });
     },
     handleCreatePlayer: function (params) {
       axios
         .post("http://localhost:5000/nbas.json", params)
         .then((response) => {
           console.log("players create", response);
           this.players.push(response.data);
         })
         .catch((error) => {
           console.log("players create error", error.response);
         });
     },
     handleShowPlayer: function (player) {
       console.log("handleShowPlayer", player);
       this.currentPlayer = player;
       this.isPlayersShowVisible = true;
     },
     handleClose: function () {
       this.isPlayersShowVisible = false;
     },
   },
};
</script>

<template>
  <main>
    <PlayersNew v-on:createPlayer="handleCreatePlayer" />
     <PlayersIndex v-bind:players="players" v-on:showPlayer="handleShowPlayer" />
     <Modal v-bind:show="isPlayersShowVisible" v-on:close="handleClose">
        <PlayersShow v-bind:player="currentPlayer" />
     </Modal>
  </main>
</template>

<style></style>
