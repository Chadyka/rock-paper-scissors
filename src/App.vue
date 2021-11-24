<template>
  <div id="app">
    <h1>Pick your weapon!</h1>
    <div class="control-wrapper">
      <ControlBtn
        class="controls"
        img="rock"
        @click.native="setPlayerChoice('rock')"
      />
      <ControlBtn
        class="controls"
        img="paper"
        @click.native="setPlayerChoice('paper')"
      />
      <ControlBtn
        class="controls"
        img="scissors"
        @click.native="setPlayerChoice('scissors')"
      />
    </div>
    <ScoreBoard
      :player-choice="player"
      :computer-choice="computer"
      :player-score="playerScore"
      :computer-score="computerScore"
      :result="lastGameResult"
    />
  </div>
</template>

<script>
import ControlBtn from "./components/ControlBtn.vue";
import ScoreBoard from "./components/ScoreBoard.vue";

export default {
  name: "app",
  components: {
    ControlBtn,
    ScoreBoard,
  },
  data() {
    return {
      player: "",
      computer: "",
      playerScore: 0,
      computerScore: 0,
      lastGameResult: "",
    };
  },
  methods: {
    setPlayerChoice(choice) {
      this.player = choice;
      this.playGame();
    },
    resetScore() {
      this.player = "";
      this.computer = "";
      this.playerScore = 0;
      this.computerScore = 0;
    },
    playGame() {
      const rand = Math.floor(Math.random() * 3);
      if (rand === 0) {
        this.computer = "rock";
      } else if (rand === 1) {
        this.computer = "paper";
      } else if (rand === 2) {
        this.computer = "scissors";
      }

      if (this.computer === this.player) {
        this.lastGameResult = "Draw!";
      } else if (this.computer === "rock" && this.player === "paper") {
        this.lastGameResult = "You won!";
        this.playerScore++;
      } else if (this.computer === "rock" && this.player === "scissors") {
        this.lastGameResult = "You lost!";
        this.computerScore++;
      } else if (this.computer === "paper" && this.player === "rock") {
        this.lastGameResult = "You lost!";
        this.computerScore++;
      } else if (this.computer === "paper" && this.player === "scissors") {
        this.lastGameResult = "You won!";
        this.playerScore++;
      } else if (this.computer === "scissors" && this.player === "rock") {
        this.lastGameResult = "You won!";
        this.playerScore++;
      } else if (this.computer === "scissors" && this.player === "paper") {
        this.lastGameResult = "You lost!";
        this.computerScore++;
      }
      // eslint-disable-next-line no-console
      console.log(this.computer);
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

html {
  background-color: lavender;
}

.control-wrapper {
  display: flex;
  width: 40%;
}
.controls {
  width: 100%;
  height: 100%;
  margin: 0 20px;
  padding: 2rem;
  border-radius: 50%;
  cursor: pointer;
}

.controls:hover {
  transform: scale(1.1);
}

.controls:nth-child(1) {
  background-color: burlywood;
}
.controls:nth-child(2) {
  background-color: turquoise;
}
.controls:nth-child(3) {
  background-color: lemonchiffon;
}
</style>
