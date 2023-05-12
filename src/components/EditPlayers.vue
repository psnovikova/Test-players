<template>
  <h1>Редактирование игроков</h1>

  <div
    v-for="item in usersLife"
    :key="item.name"
    class="row"
  >
      <input id="name" v-model="item.name">
      <a class="button" href="#" @click.prevent="minusLife(item)">-</a>
      <span class="lifeCount">{{item.life}}</span>
      <a class="button" href="#" @click.prevent="plusLife(item)">+</a>
  </div>
  
  <h2>Рейтинг</h2>
  <table>
    <tr
    v-for="(item, index) in rating"
    :key="index"
    >
    <td v-text="`${index + 1}`"></td>
    <td v-text="`У игрока <b>${item.name}</b> ${item.life} жизней`"></td>
  </tr>
  </table>
</template>

<script>
export default {
  name: 'LifeCounter',

  props: {
    playersList: {
      type: Array
    },
  },
  
  data () {
    return {
    };
  },
  
  created() {
    for (let i = 0; i < this.playersList; i++) {
      this.usersLife.push({
        name: this.playersList.name,
        life: this.playersList.life
      });
    }
  },
  
  computed: {
    usersLife () {
      return [...this.playersList]
    },
    rating () {
      let places = this.usersLife;
  
      places.sort((a, b) => b.life - a.life);
     
      return places;
    }
  },
  
  methods: {
    plusLife (item) {
      item.life++;
    },

    minusLife (item) {
      item.life--;
    }
  },
}
</script>

<style lang="scss">
    .row {
        display: flex;
        align-items: center;
        margin-top: 20px;

        input {
            margin-right: 12px;
            width: 100%;
            height: 24px;
        }

        .button {
          width: 24px;
          height: 24px;
        }

        .life {
          margin: 0 12px;
        }
    }

    table {
      width: 100%;

      td {
        border: 1px solid #2c3e50;
      }
    }
</style>