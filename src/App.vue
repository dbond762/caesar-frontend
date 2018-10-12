<template>
  <div id="app">
    <AppLegend/>
    <AppCrypter @response="res => { resp = res }"/>
    <AppChart :freqs="resp.freqs"/>
  </div>
</template>

<script>
import AppLegend from './components/AppLegend.vue'
import AppCrypter from './components/AppCrypter.vue'
import AppChart from './components/AppChart'

export default {
  name: 'app',
  components: {
    AppLegend,
    AppCrypter,
    AppChart
  },
  data: function() {
    return {
      resp: {
        freqs: []
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
