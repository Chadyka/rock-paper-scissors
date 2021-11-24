<template>
  <div class="score-root">
    <h1>{{ result }}</h1>
    <div class="score">
      <div>
        <h2>Player</h2>
        <img
          v-if="playerChoice"
          :src="require(`@/assets/${playerChoice}.png`)"
        />
      </div>
      <h2>{{ playerScore }}</h2>
      <h2>:</h2>
      <h2>{{ computerScore }}</h2>
      <div>
        <h2>Comp</h2>
        <img
          v-if="computerChoice"
          :src="require(`@/assets/${computerChoice}.png`)"
        />
      </div>
    </div>
    <button class="reset-btn" @click="$parent.resetScore()">Reset</button>
  </div>
</template>

<script>
export default {
  name: "ScoreBoard",
  props: {
    playerChoice: String,
    computerChoice: String,
    playerScore: {
      type: Number,
      default() {
        return 0;
      },
    },
    computerScore: {
      type: Number,
      default() {
        return 0;
      },
    },
    result: String,
  },
};
</script>

<style scoped>
.score-root {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 10rem;
}

.score {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 32px;
}

.score h2 {
  margin: 0 1rem;
}

.score img {
  width: 100px;
  height: 100px;
  margin-left: 50px;
  margin-right: 50px;
}

.reset-btn {
  margin-top: 2.5rem;
  padding: 1rem 2rem;
  font-size: 24px;
  color: white;
  background-color: cornflowerblue;
  border-radius: 50%;
  cursor: pointer;
}
</style>
