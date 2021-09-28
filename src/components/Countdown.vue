<template>
  <div>
    <h1>Wuhiuuu</h1>
    <p>{{d}}d {{h}}h {{m}}m {{s}}s</p>
  </div>
</template>

<script>
export default {
  name: "Countdown",
  props: {
    d: {
      type: Number,
      default: 0
    },
    h: {
      type: Number,
      default: 0
    },
    m: {
      type: Number,
      default: 0
    },
    s: {
      type: Number,
      default: 0
    },
  },
}
</script>

<style scoped>
</style>