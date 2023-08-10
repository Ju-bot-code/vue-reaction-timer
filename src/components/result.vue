<template>
  <div class="p-4 capitalize border rounded-md">
    <p>
      your reaction time score is <span class="text-green-400">{{ score }} </span> mili seconds !
    </p>
    <p class="text-lg font-semibold text-center text-orange-500 capitalize ">{{ rank }}...!</p>
  </div>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: 0
    }
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Ninja Fingers'
    } else if (this.score < 400) {
      this.rank = 'Rapid Reflexes'
    } else {
      this.rank = 'Snail pace'
    }
  }
}
</script>

<style></style>
