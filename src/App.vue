<template>
  <div id="app">
    <AppLegend/>
    <AppCrypter @response="res => { resp = res }"/>
    <AppChart :freqs="resp.freqs"/>
    <AppMessage :shift="resp.shift"/>
  </div>
</template>

<script>
import AppLegend from './components/AppLegend.vue'
import AppCrypter from './components/AppCrypter.vue'
import AppChart from './components/AppChart.vue'
import AppMessage from './components/AppMessage.vue'

export default {
  name: 'app',
  components: {
    AppLegend,
    AppCrypter,
    AppChart,
    AppMessage
  },
  data: function() {
    return {
      resp: {
        freqs: [],
        shift: 0
      }
    }
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
