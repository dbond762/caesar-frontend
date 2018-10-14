<template>
  <div class="app-chart">
    <canvas id="chart" width="700" height="200"></canvas>
  </div>
</template>

<script>
import Chart from 'chart.js'

export default {
  name: 'AppChart',
  props: {
      freqs: Array
  },
  watch: {
    freqs: function (val) {
      let chart = document.querySelector('#chart')

      Chart.defaults.global.defaultFontFamily = 'Avenir'
      Chart.defaults.global.defaultFontSize = 18
      Chart.defaults.global.defaultColor = '#2c3e50'

      for (let i = 0; i < val.length; i++) {
        val[i] = val[i].toFixed(5)
      }

      let barChart = new Chart(chart, {
        type: 'bar',
        data: {
          labels: [
            'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K',
            'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V',
            'W', 'X', 'Y', 'Z'
          ],
          datasets: [{
            label: 'Частотная диаграмма',
            backgroundColor: '#2c3e50',
            data: val
          }]
        }
      })
    }
  }
}
</script>

<style scoped>
.app-chart {
    height: 200px;
    width: 700px;
    margin: 30px;
}
@media screen and (max-width: 800px) {
  .app-chart {
    display: none;
  }
}
</style>
