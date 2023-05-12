<template>
  <CreatePlayer @players-list="createdPlayers" />
  <EditPlayers :playersList="playersList" />
</template>

<script>
import CreatePlayer from './components/CreatePlayer.vue'
import EditPlayers from './components/EditPlayers.vue'

export default {
  name: 'App',
  components: {
    CreatePlayer,
    EditPlayers
  },
  data() {
    return {
      playersList: []
    }
  },

  created() {
    
  },

  methods: {
    createdPlayers(list) {
      this.playersList = list;
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 600px;
}
</style>
