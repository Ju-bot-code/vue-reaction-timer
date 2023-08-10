<template>
  <div
    @click="stopTimer"
    v-if="showBlock"
    class="group bg-green-100 hover:bg-green-200 rounded-lg w-[200px] h-[200px] flex justify-center items-center"
  >
    <p class="font-medium text-[18px] text-green-700 group-hover:text-green-900">Click me</p>
  </div>
  <!-- {{ delay }} -->
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTimer: 0
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.runtimer()
    }, this.delay)
  },
  methods: {
    runtimer() {
      this.timer = setInterval(() => {
        this.reactionTimer += 10
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit('end',this.reactionTimer)
    }
  }
}
</script>

<style></style>
