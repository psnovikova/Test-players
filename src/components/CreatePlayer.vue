<template>
    <h1>Добавить нового игрока</h1>
    <div class="row">
        <input id="name" type="text" v-model="players_name" placeholder="Имя"/>
        <input id="life" type="number" v-model="players_life" placeholder="Жизней" />
        <button type="button" v-on:click="createPlayer">Создать</button>
    </div>
</template>


<script>
export default {
  name: 'CreatePlayer',
  
  data () {
    return {
      players: [],
      players_name: '',
      players_life: ''
    };
  },
  
  methods: {
    createPlayer() {

        if(this.players_name === '' || this.players_name === undefined) {
            alert('Укажите имя');
            return;
        }

        if(this.players_life === '' || this.players_life === undefined) {
            alert('Укажите количество жизней');
            return;
        }

        if(this.players_life <= 0) {
            alert('Значение не может быть больше нуля');
            return;
        }

        this.players.push({
            'name': this.players_name,
            'life': this.players_life,
        })

        this.players_name = '';
        this.players_life = '';

        this.$emit('players-list', this.players);
    }
  },
}
</script>

<style lang="scss">
    .row {
        display: flex;
        margin-top: 20px;

        input {
            margin-right: 12px;
            width: 100%;
            height: 24px;
        }

        button {
            width: 70px;
        }
    }

    #life {
        width: 70px;
    }
</style>
