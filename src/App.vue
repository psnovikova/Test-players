<template>
  <div>
    <div>
      <button
        class="tab-btn"
        :class="{ active: currentView === 'create' }"
        @click="currentView = 'create'"
      >
        Создание
      </button>
      <button
        class="tab-btn"
        :class="{ active: currentView === 'edit' }"
        @click="currentView = 'edit'"
      >
        Редактирование
      </button>
    </div>

    <div v-if="currentView === 'create'">
      <CreatePlayer @players-list="createdPlayers" />
    </div>
    <div v-else>
      <EditPlayers :playersList="playersList" />
    </div>
  </div>
</template>

<script>
import CreatePlayer from "./components/CreatePlayer.vue";
import EditPlayers from "./components/EditPlayers.vue";

export default {
  name: "App",
  components: {
    CreatePlayer,
    EditPlayers,
  },
  data() {
    return {
      playersList: [],
      currentView: "create",
    };
  },

  created() {},

  methods: {
    createdPlayers(list) {
      this.playersList = list;
    },
  },
};
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

.tab-btn {
  padding: 10px 20px;
  margin: 0 10px;
  cursor: pointer;
  font-size: 16px;
}

.tab-btn.active {
  background-color: #00bd69;
  color: #fff;
}
</style>
