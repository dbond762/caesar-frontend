<template>
  <div class="app-crypter">
    <textarea v-model="input" class="io-area" cols="30" rows="10"></textarea>
    <div class="controls">
      <ShiftInput @change="sh => { shift = sh }"/>
      <input type="button" value="Зашифровать" @click="send(true)">
      <input type="button" value="Расшифровать" @click="send(false)">
    </div>
    <textarea v-model="output" class="io-area output" cols="30" rows="10" readonly></textarea>
  </div>
</template>

<script>
import axios from "axios"

import ShiftInput from "./ShiftInput.vue"

export default {
  name: 'AppCrypter',
  components: {
    ShiftInput
  },
  data: function() {
    return {
      input: 'If the radiance of a thousand suns were to burst at once into the sky, that would be like the splendor of the mighty one. Now I am become Death, the destroyer of worlds.',
      output: '',
      shift: 3
    }
  },
  methods: {
    send: function(encode) {
      axios.post(`http://localhost:8000`, {
        text: this.input,
        shift: this.shift,
        encode: encode
      })
      .then(resp => {
        this.output = resp.data.text
        this.$emit('response', resp.data)
      })
      .catch(e => {
        console.log(e)
      })
    }
  }
}
</script>

<style scoped>
.app-crypter {
  display: flex;
}
.controls {
  display: flex;
  flex-direction: column;
  align-self: flex-end;
  width: 180px;
}
.io-area {
  width: 100%;
  resize: none;
  border: 2px solid #333;
  border-radius: 10px;
  padding: 10px;
  background: #eee;
  margin: 0 20px;
}
.output {
  cursor: not-allowed;
}
</style>
