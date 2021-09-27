<template>
  <div id="form" class="p-4 m-auto mt-4">
    <div v-if="!countdownStarted">
      <h1 class="text-center">When is your party?</h1>
      <input type="time" v-model="current_time">
      <input type="date" v-model="current_date">
      <button @click="createDate()" class="btn btn-primary d-block m-auto mt-4">Start countdown</button>
    </div>
    <Countdown v-if="countdownStarted" :d="dLeft" :h="hLeft" :m="mLeft" :s="sLeft"></Countdown>
  </div>
</template>

<script>
import Countdown from "@/components/Countdown";

export default {
  name: "Form",
  components: {
    Countdown
  },
  data: function () {
    let countdownStarted = false
    if(localStorage.getItem("countDate") !== null) {
      countdownStarted = true
    }
    return {
      current_date: Date,
      current_time: Number,
      countdownStarted: countdownStarted,
      dLeft: 0,
      hLeft: 0,
      mLeft: 0,
      sLeft: 0
    }
  },
  created() {
    if (this.countdownStarted === true) {
      let countDateStored = localStorage.getItem('countDate');
      countDateStored = new Date(countDateStored)
      console.log(countDateStored)
      this.startCountdown(countDateStored)
    }
  },
  methods: {
    createDate() {
      let hrs = this.current_time.substring(0, 2)
      let hrsInt = parseInt(hrs)
      let mins = this.current_time.substring(3, 5)
      let minsInt = parseInt(mins)
      let countDate = new Date(this.current_date)
      countDate.setHours(countDate.getHours() + hrsInt)
      countDate.setMinutes(countDate.getMinutes() + minsInt)
      localStorage.setItem("countDate", countDate)
      this.startCountdown(countDate)
    },
    startCountdown(countDate) {
      console.log(countDate)
      let self = this;
      let countdown = setInterval(function () {
          let date = new Date().getTime()
          let distance = countDate - date;
          self.dLeft = Math.floor(distance / (1000 * 60 * 60 * 24));
          self.hLeft = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
          self.mLeft = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
          self.sLeft = Math.floor((distance % (1000 * 60)) / 1000);
          if(distance < 0) {
            clearInterval(countdown)
          }
      }, 1000)
      this.countdownStarted = true
    }
  }
}
</script>

<style scoped>
#form {
  background-color: #fff;
  border-radius: 12px;
  width: 95%;
  max-width: 900px;
}
#form h1 {
  color: #202020;
}
</style>