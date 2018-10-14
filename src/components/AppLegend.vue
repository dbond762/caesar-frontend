<template>
  <div class="app-legend">
    <h1>Шифр Цезаря</h1>
  </div>
</template>

<script>
export default {
  name: 'AppLegend'
}
</script>

<style scoped>
.app-legend {
  margin: 20px;
  font-size: 16px;
}
@media screen and (max-width: 360px) {
  .app-legend {
    font-size: 13px;
  }
}
</style>
