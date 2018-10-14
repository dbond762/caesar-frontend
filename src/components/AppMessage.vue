<template>
  <div class="app-message" :class="{ hide: !isActive }">
    <div v-if="resp.isAnalyzed === false" class="text">Текст слишком мал для анализа</div>
    <div v-else-if="resp.shift !== 0" class="text">Это зашифрованный текст. Смещение равно <span class="link" @click="$emit('setShift', resp.shift)">{{resp.shift}}</span></div>
    <div v-else class="text">Это не зашифрованный текст</div>
    <div class="close" @click="isActive = false">x</div>
  </div>
</template>

<script>
export default {
  name: 'AppMessage',
  props: {
      resp: Object
  },
  data: function() {
    return {
      isActive: false
    }
  },
  watch: {
    resp: function (val) {
      this.isActive = val.text !== ''
    }
  }
}
</script>

<style scoped>
.app-message {
  background: #fdffef;
  border: 1px solid #fdffef;
  border-radius: 10px;
  padding: 10px;
  box-shadow: 1px 1px 5px 0px #2c3e5080;
  margin: 20px;
  position: relative;
  opacity: 1;
  transition: opacity 0.3s ease-out;
}
.hide {
  opacity: 0;
}
.text {
  display: inline-block;
  max-width: 85%;
}
.link {
  text-decoration: underline;
}
.link:hover {
  cursor: pointer;
  color: #79a2d2;
}
.close {
  display: inline-block;
  position: absolute;
  right: 10px;
  color : #300;
  padding: 0 10px;
}
.close:hover {
  cursor: pointer;
  color: #900;
}
</style>
