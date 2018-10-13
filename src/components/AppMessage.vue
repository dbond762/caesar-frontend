<template>
  <div class="app-message">
    <span v-if="shift !== 0">Сдвиг {{shift}}</span>
    <span v-else>Это не зашифрованный текст</span>
  </div>
</template>

<script>
export default {
  name: 'AppMessage',
  props: {
      shift: Number
  }
}
</script>

<style scoped>
.app-message {
  background: #eee;
  border: 2px solid #333;
  border-radius: 10px;
  padding: 10px;
}
</style>
