<template>
  <div>
    <h1 class="text-center p-3">Your party starts in</h1>
    <div id="timer">
      <div class="number-list">
        <div class="item">{{d}}</div>
        <div class="item">{{h}}</div>
        <div class="item">{{m}}</div>
        <div class="item">{{s}}</div>
      </div>
      <div class="unit-list">
        <div class="item">{{ dayText }}</div>
        <div class="item">Hour</div>
        <div class="item">Minutes</div>
        <div class="item">Seconds</div>
      </div>
    </div>
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
  data: function (){
    return {
      dayText: "days"
    }
  },
  watch: {
    d: function () {
      if(this.d === 1){
        this.dayText = "day"
      }
    }
  }
}
</script>

<style scoped>
</style>