<template>
  <section class="status">
    <div class="status__buttons">
      <button @click="start">
        {{ gameStatus ? "restart" : "play" }}
      </button>
      <button @click="pause">
        {{ isGamePaused ? "continue" : "pause" }}
      </button>
    </div>
  </section>
</template>

<script>
import * as status from "../unit/status"
import { mapActions, mapMutations, mapState } from 'vuex';
export default {
  computed: {
    ...mapState([
      "",
      "gameStatus",
      "isGamePaused"
    ]),

  },
  methods: {
    ...mapActions(['initGame']),
    ...mapMutations(['toggleSimulation']),

    start() {
      if (this.gameStatus == "") {
        status.startGame()
      } else {
        status.restartGame();
      }
    },

    pause() {
      if (this.isGamePaused) {
        status.contineuGame();
      } else {
        status.pauseGame();
      }
    },
  }
}
</script>

<style lang="scss" scoped>
.status {
  display: flex;
  margin-left: auto;
  margin-right: auto;
}
</style>
