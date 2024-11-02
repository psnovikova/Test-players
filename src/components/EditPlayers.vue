<template>
  <h1>Редактирование игроков</h1>

  <div v-for="(item, index) in playersList" :key="index" class="row">
    <input id="name" v-model="item.name" placeholder="Имя" />
    <div class="count-container">
      <button
        :disabled="!item.life"
        class="count-btn"
        @click.prevent="minusLife(item)"
      >
        -
      </button>
      <span class="lifeCount">{{ item.life }}</span>
      <button class="count-btn" @click.prevent="plusLife(item)">+</button>
    </div>
  </div>

  <h2>Рейтинг</h2>
  <table>
    <tr v-for="(item, index) in rating" :key="index">
      <td v-text="`${index + 1}`"></td>
      <td>
        У игрока <b>{{ item.name }}</b> {{ item.life }} жизней
      </td>
    </tr>
  </table>
</template>

<script>
export default {
  name: "EditPlayers",

  props: {
    playersList: {
      type: Array,
    },
  },

  data() {
    return {};
  },

  computed: {
    rating() {
      return [...this.playersList].sort((a, b) => b.life - a.life);
    },
  },

  methods: {
    plusLife(item) {
      item.life++;
    },

    minusLife(item) {
      item.life--;
    },
  },
};
</script>

<style lang="scss">
.row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 12px;

  input {
    margin-right: 8px;
    width: 60%;
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

  .count-container {
    display: flex;
    justify-content: space-between;
    min-width: 150px;
    .count-btn {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 28px;
      height: 28px;
      margin: 0 8px;
      border: none;
      background-color: #3a86ff;
      color: #fff;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s;
      &:hover {
        background-color: #005fcb;
      }
      &:disabled {
        background-color: #cccccc;
        cursor: not-allowed;
        &:hover {
          background-color: #cccccc;
        }
      }
    }

    .lifeCount {
      font-size: 18px;
      font-weight: bold;
    }
  }
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;

  td {
    padding: 8px;
    border: 1px solid #cccccc;
    text-align: center;
  }

  tr:nth-child(even) {
    background-color: #f9f9f9;
  }
}
</style>
