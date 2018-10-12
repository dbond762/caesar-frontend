<template>
  <div class="app-chart">
    <div class="bar" v-for="(f, i) in freqs" :style="`height: ${f*100}%`" :key="i"></div>
  </div>
</template>

<script>
export default {
  name: 'AppChart',
  props: {
      freqs: Array
  }
}
</script>

<style scoped>
.app-chart {
    height: 200px;
    margin: 30px;
}
.bar {
    display: inline-block;
    width: 20px;
    background: #000;
    margin: 0 5px;
}
</style>
