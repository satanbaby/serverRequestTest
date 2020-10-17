<template>
<dir class="card">
  <chart :request="state.count"/>
  <div class="details">
    <h1>{{ state.count }}</h1>
    <p>{{ state.info.timespan }}ms, {{state.info.size}}byte</p>
    <p v-if="!state.isOpenInput" @click="state.isOpenInput = !state.isOpenInput;this.$refs.input_ref.focus()">{{ state.sendUri }}</p>
    <input v-else
      @keydown.enter="state.isOpenInput = !state.isOpenInput"
      type="text"
      ref="input_ref"
      v-model="state.sendUri">
    <input type="button" value="Send" @click="sendAjax">
  </div>
</dir>
</template>

<script>
import { reactive } from 'vue'
import axios from 'axios'
import chart from './chart.vue'

export default {
  props: {
    sendUri: String
  },
  components: {
    chart
  },
  setup (props) {
    const state = reactive({
      count: 0,
      sendUri: props.sendUri,
      isOpenInput: false,
      info: {
        timespan: 0,
        size: 0
      }
    })

    function sendAjax () {
      const _timespan = Date.now()
      state.count++
      axios.get(state.sendUri)
        .then(resposne => {
          state.count--
          state.info.timespan = Date.now() - _timespan
          state.info.size = resposne.headers['content-length']
        })
        .catch(error => {
          alert(error)
        })
    }

    return {
      state,
      sendAjax
    }
  }
}
</script>

<style lang="scss" scoped>
p { word-break: break-all }
.card{
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background-color: whitesmoke;
  margin: 30px;
  text-align: center;
  width: 400px;
  height: 400px;
  box-shadow: 0 0 30px #333;
  border-radius: 20px;
  overflow: hidden;
  .details{
    p{
      margin: 10px;
    }
    input[type="text"]{
      height: 30px;

    }
    input[type="button"]{
      background-color: #5a9;
      height: 60px;
      width: 100%;
      border: none;
      transition-duration: .3s;
      &:hover{
        cursor: pointer;
        background-color: darken(#5a9, 10%);
      }
    }
  }
}
</style>
