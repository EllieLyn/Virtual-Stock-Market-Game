<template>
  <div id="newGame">
      <form>
          <h1>Create a New Game</h1>
          <div id="form-name-game">
              <label for="name-game">Name Game:</label>
              <input v-model="newGame.nameOfGame" type="text" id="game-name" />
          </div>
          <div>
              <label for="end-date">Choose End Date</label>
              <input v-model="newGame.endDate" type="date" id="end-date" />
          </div>
          <button v-on:click.prevent="createNewGame" id="create">Create Game</button>
          <!-- <router-link v-bind:to="{name: 'InvitePlayers', params:{id:this.$store.gameId}}" id="invite-tag" v-if="$store.state.token != ''"><button id="Create">Create Game</button></router-link> -->

      </form>
  </div>
</template>

<script scoped>
import GameService from '../services/GameService';

export default {
    name: "NewGame",
    data() {
      return {
        newGame: {
          nameOfGame: "",
          ownerName: this.$store.state.user.username,
          gameId: 0,
        } 
      }
    },
    methods: {
      createNewGame() {
        GameService.createGame(this.newGame).then((response) => {
          this.gameId = response.data
          console.log(response.data)
          if(response.status == 201){
            this.$router.push(`/invite_players${response.data}`)
          }
        })
      }
    },
}
</script>

<style scoped>
label {
  margin-right: 0.5rem;
}
#newGame {
  width: 100vw;
  height: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}
form {
  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  width:30em;
  height: auto;
  text-align: center;
}
form h1 {
  padding-top: 1rem;
  color:black;
  font-size: 1.35rem;
}
form input:first-of-type {
  margin-top: 2rem;
}
#invite {
    background-color: rgb(90, 212, 90);
    padding-top: 10px;
    padding-bottom: 10px;
    padding-left: 30px;
    padding-right: 30px;
    border-radius: 20px;
    border-style: none;
    margin-bottom: 15px;
    margin-left: 10px;
    margin-right: 10px;
  }
  #invite:hover {
    background-color: rgb(43, 114, 43);
    font-weight: bold;
  }
  th {
    padding-left: 20px;
    padding-right: 20px;
    padding-bottom: 15px;
  }
  td {
    padding-bottom: 5px;
  }
  #invite-players {
    grid-area: bin1;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  form button {
  margin-top: 2rem;
  padding-left: 3rem;
  padding-right: 3rem;
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
  background-color: rgb(56, 216, 56);
  border-radius: 1rem;
  border-style: none;
  box-shadow: 2px 2px 4px;
  font-weight: bold;
  margin-bottom: 20px;
}
form button:hover {
  background-color: rgb(26, 116, 26);
}

</style>