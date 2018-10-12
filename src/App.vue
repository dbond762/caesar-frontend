<template>
  <div id="app">
    <AppLegend/>
    <AppCrypter/>
  </div>
</template>

<script>
import AppLegend from './components/AppLegend.vue'
import AppCrypter from "./components/AppCrypter.vue";

export default {
  name: 'app',
  components: {
    AppLegend,
    AppCrypter
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 60px;
}
</style>
