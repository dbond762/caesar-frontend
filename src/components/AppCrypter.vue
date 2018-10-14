<template>
  <div class="app-crypter">
    <textarea v-model="input" class="io-area" cols="30" rows="10"></textarea>
    <div class="controls">
      <input type="number" class="input" v-model.number="shift" @change="$emit('setShift', shift)">
      <input class="btn" type="button" value="Зашифровать" @click="send(true)">
      <input class="btn" type="button" value="Расшифровать" @click="send(false)">
    </div>
    <textarea v-model="output" class="io-area output" cols="30" rows="10" readonly></textarea>
  </div>
</template>

<script>
import axios from "axios"

export default {
  name: 'AppCrypter',
  props: {
    shift: Number
  },
  data: function() {
    return {
      input: 'Ro cqn ajmrjwln xo j cqxdbjwm bdwb fnan cx kdabc jc xwln rwcx cqn bth, cqjc fxdum kn urtn cqn byunwmxa xo cqn vrpqch xwn. Wxf R jv knlxvn Mnjcq, cqn mnbcaxhna xo fxaumb.',
      output: ''
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
.input {
  margin: 5px;
  border: 1px solid #fff;
  border-radius: 5px;
  padding: 5px;
  box-shadow: 1px 1px 5px 0px #2c3e5080;
}
.btn {
  background: #d1e1f5;
  margin: 5px;
  border: 1px solid #d1e1f5;
  border-radius: 5px;
  padding: 5px;
  box-shadow: 1px 1px 5px 0px #2c3e5080;
}
.btn:hover {
  cursor: pointer;
}
.io-area {
  width: 100%;
  resize: none;
  border: 1px solid #fdffef;
  border-radius: 10px;
  padding: 10px;
  box-shadow: 1px 1px 5px 0px #2c3e5080;
  background: #fdffef;
  margin: 0 20px;
}
.output {
  cursor: not-allowed;
}
@media screen and (max-width: 820px) {
  .app-crypter {
    flex-direction: column;
    padding-right: 60px;
  }
  .controls {
    align-self: center;
    margin: 10px 10px 10px 70px;
  }
}
</style>
