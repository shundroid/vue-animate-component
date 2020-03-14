<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    value: Boolean,
  },
  watch: {
    value() {
      if (this.value) {
        this.playAnimation()
      }
    }
  },
  methods: {
    getKeyframes() {
      const keyframes = []
      for (let child of this.$children) {
        keyframes.push(child.$attrs)
      }
      return keyframes
    },
    getOptions() {
      return this.$attrs
    },
    playAnimation() {
      const keyframes = this.getKeyframes()
      const options = this.getOptions()
      this.$el.parentNode.animate(keyframes, options).addEventListener('finish', () => {
        this.$emit('input', false)
      })
    }
  }
}
</script>

<style scoped>
div {
  display: none;
}
</style>