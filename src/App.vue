<template>
  <section class="w-screen h-screen">
    <div class="flex flex-col items-center justify-center h-full space-y-6">
      <h1 class="text-2xl font-semibold">Reaction timer game</h1>
      <button
        :disabled="isPlaying"
        @click="play"
        class="px-4 py-1 text-gray-600 capitalize bg-transparent border rounded-full disabled:bg-transparent disabled:text-gray-200 hover:bg-gray-200"
      >
        play
      </button>
      <Result v-if="showResult" :score="score"></Result>

      <GameBlock @end="endGame" v-if="isPlaying" :delay="delay" />
    </div>
  </section>
</template>
<script>
import GameBlock from './components/gameBlock.vue'
import Result from './components/result.vue'
export default {
  components: { GameBlock, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    play() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTimer) {
      this.score = reactionTimer
      this.isPlaying = false
      this.showResult = true
    }
  }
}
</script>

<style scoped></style>
