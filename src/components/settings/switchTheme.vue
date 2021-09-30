<template>
    <div>
      <select class="form-select form-select-sm" aria-label=".form-select-sm example" v-model="theme">
        <option selected>Change theme here</option>
        <option value="blue">Blue</option>
        <option value="orange">Orange</option>
      </select>
    </div>
</template>

<script>

export default {
  name: "switchTheme",
  components: {
  },
  data: function () {
    let theme = localStorage.getItem("theme")
    console.log(theme)
    if(theme === null) {
      theme = "orange"
      console.log(theme)
    }
    return {
      theme: theme,
    }
  },
  created() {
    document.body.classList.add(this.theme)
  },
  watch: {
    theme: function () {
      switch (this.theme) {
        case "blue":
          document.body.classList.add("blue")
          document.body.classList.remove("orange")
          break;
        case "orange":
          document.body.classList.add("orange")
          document.body.classList.remove("blue")
          break;
        default:
          document.body.classList.add("blue")
          document.body.classList.remove("orange")
          break;
      }
    }
  }
}
</script>

<style scoped>

</style>