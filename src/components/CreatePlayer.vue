<template>
  <h1>Добавить нового игрока</h1>
  <div class="row">
    <input id="name" type="text" v-model="players_name" placeholder="Имя" />
    <input
      id="life"
      type="number"
      v-model.number="players_life"
      placeholder="Жизней"
    />
    <button type="button" v-on:click="createPlayer">Создать</button>
  </div>
</template>

<script>
export default {
  name: "CreatePlayer",

  data() {
    return {
      players: [],
      players_name: "",
      players_life: "",
    };
  },

  methods: {
    createPlayer() {
      if (!this.players_name) {
        alert("Укажите имя");
        return;
      }

      if (!this.players_life) {
        alert("Укажите количество жизней");
        return;
      }

      if (this.players_life <= 0) {
        alert("Количество жизней должно быть больше нуля");
        return;
      }

      this.players.push({
        name: this.players_name,
        life: this.players_life,
      });

      this.players_name = "";
      this.players_life = "";

      this.$emit("players-list", this.players);
    },
  },
};
</script>

<style lang="scss">
.row {
  display: flex;
  margin-top: 20px;
  align-items: center;

  input {
    margin-right: 12px;
    width: 100%;
    height: 30px;
    padding: 4px 8px;
    border: 1px solid #cccccc;
    border-radius: 4px;
    font-size: 16px;
    transition: border-color 0.3s;
    &:focus {
      border-color: #3a86ff;
      outline: none;
    }
  }

  button {
    height: 34px;
    padding: 0 12px;
    background-color: #3a86ff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
    &:hover {
      background-color: #005fcb;
    }
  }
}
</style>
