<template>
  <div class="app-crypter">
    <textarea v-model="input" class="io-area" cols="30" rows="10"></textarea>
    <ShiftInput @change="sh => { shift = sh }"/>
    <input type="button" value="<-" @click="send(false)">
    <input type="button" value="->" @click="send(true)">
    <textarea v-model="output" class="io-area" cols="30" rows="10" readonly></textarea>
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
      input: '',
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
.io-area {
  resize: none;
}
</style>
