<template>
  <div id="app">
    <Header></Header>
    <Form></Form>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Form from './components/Form.vue'


export default {
  name: 'App',
  components: {
    Header,
    Form,
  }
}
</script>

<style>
body {
  background-color: #69346E !important;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  padding-top: 60px;
  background-color: #69346E;
}
</style>
