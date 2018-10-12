<template>
  <div class="shift-input">
    <input type="number" class="input" @change="$emit('change', shift)" v-model.number="shift">
  </div>
</template>

<script>
export default {
  name: 'ShiftInput',
  data: function() {
    return {
      shift: 3
    }
  }
}
</script>

<style scoped>

</style>
