<template>
  <div id="form" class="p-4 m-auto mt-4">
    <div v-if="!countdownStarted">
      <h1 class="text-center p-3">When is your party?</h1>
      <input class="form-control mt-2 mb-4" type="date" v-model="current_date">
      <input class="form-control" type="time" v-model="current_time">
      <button @click="createDate()" class="btn button d-block m-auto mt-4">start countdown</button>
    </div>
    <div v-if="countdownStarted && !countdownEnd">
      <Countdown :d="dLeft" :h="hLeft" :m="mLeft" :s="sLeft"></Countdown>
      <button @click="stopCountdown()" class="btn button d-block m-auto mt-4">stop countdown</button>
    </div>
    <div v-if="countdownEnd">
      <end-countdown></end-countdown>
      <button @click="stopCountdown()" class="btn button d-block m-auto mt-4">new countdown</button>
    </div>
  </div>
</template>

<script>
import Countdown from "@/components/Countdown";
import endCountdown from "@/components/endCountdown";

export default {
  name: "Form",
  components: {
    Countdown,
    endCountdown
  },
  data: function () {
    let countdownStarted = false
    if(localStorage.getItem("countDate") !== null) {
      countdownStarted = true
    }
    return {
      countdown: function (){},
      current_date: Date,
      current_time: Number,
      countdownStarted: countdownStarted,
      dLeft: 0,
      hLeft: 0,
      mLeft: 0,
      sLeft: 0,
      countdownEnd: false,
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
      hrsInt = hrsInt - 2
      let mins = this.current_time.substring(3, 5)
      let minsInt = parseInt(mins)
      let countDate = new Date(this.current_date)
      countDate.setHours(countDate.getHours() + hrsInt)
      countDate.setMinutes(countDate.getMinutes() + minsInt)
      localStorage.setItem("countDate", countDate)
      this.startCountdown(countDate)
    },
    startCountdown(countDate) {
      let self = this;
      this.countdown = setInterval(function () {
          let date = new Date().getTime()
          let distance = countDate - date;
          self.dLeft = Math.floor(distance / (1000 * 60 * 60 * 24));
          self.hLeft = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
          self.mLeft = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
          self.sLeft = Math.floor((distance % (1000 * 60)) / 1000);
          if(distance < 0) {
            clearInterval(self.countdown)
            self.countdownEnd = true
          }
      }, 1000)
      this.countdownStarted = true
    },
    stopCountdown() {
      this.countdownEnd = false
      this.countdownStarted = false
      localStorage.removeItem("countDate")
      clearInterval(this.countdown)
    },
  }
}
</script>

<style scoped>

</style>