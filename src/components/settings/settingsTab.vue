<template>
  <div>
    <h1><font-awesome-icon class="font-icon"  icon="cog" /> Settings</h1>
    <switchTheme></switchTheme>
  </div>
</template>

<script>
import {FontAwesomeIcon} from '@fortawesome/vue-fontawesome';
import {library} from '@fortawesome/fontawesome-svg-core';
import {faCog} from '@fortawesome/free-solid-svg-icons/faCog';
import switchTheme from "@/components/settings/switchTheme";

library.add(faCog)
export default {
  name: "settingsTab",
  components: {
    switchTheme,
    FontAwesomeIcon
  }
}
</script>

<style scoped>

</style>