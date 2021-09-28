<template>
  <div id="footer">
    <h2 class="text-center pt-3 pb-5">How do i start a countdown?</h2>
    <div class="d-flex p-5 justify-content-between container m-auto footer-captions text-center">
      <div class="footer-caption p-2">
        <h3 class="pt-1"><font-awesome-icon icon="calendar-alt" /> Pick a date</h3>
        <p>Pick the date you are waiting the most for</p>
      </div>
      <div class="footer-caption p-2">
        <h3 class="pt-1"><font-awesome-icon icon="clock" /> Pick the time</h3>
        <p>Pick the time your event is supposed to start</p>
      </div>
      <div class="footer-caption p-2">
        <h3 class="pt-1"><font-awesome-icon icon="cocktail" /> Press the button..</h3>
        <p class="">and wait for your special date to come!</p>
      </div>
    </div>
    <div class="d-flex justify-content-center">
      <hr />
    </div>
  </div>
</template>

<script>
import {FontAwesomeIcon} from '@fortawesome/vue-fontawesome';
import {library} from '@fortawesome/fontawesome-svg-core';
import {faCalendarAlt} from '@fortawesome/free-solid-svg-icons/faCalendarAlt';
import {faClock} from '@fortawesome/free-solid-svg-icons/faClock';
import {faCocktail} from '@fortawesome/free-solid-svg-icons/faCocktail';


library.add(faCalendarAlt, faClock, faCocktail)

export default {
  name: "Footer",
  components: {FontAwesomeIcon},
}
</script>

<style scoped>

</style>