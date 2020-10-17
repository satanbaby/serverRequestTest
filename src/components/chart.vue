<template>
  <div id="chart">
    <!-- <div
      class="area"
      v-for="i in 20" :key="i">
    </div> -->
    <div id="pointer"></div>
  </div>
</template>

<script>
import { reactive } from 'vue'

export default {
  props: {
    request: Number
  },
  setup (props) {
    const state = reactive({
      count: 0,
      sendUri: props.sendUri,
      isOpenInput: false
    })
    return state
  },
  computed: {
    requestCount () {
      // `this` points to the vm instance
      return this.author.books.length > 0 ? 'Yes' : 'No'
    }
  }
}
</script>

<style lang="scss" scope>
$base-color: #630;
#chart{
  display: block;
  position: relative;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  outline: black 1px solid;
}
#pointer{
  height: 0;
  width: 150px;
  border: 2px solid red;
}
.area{
  width: 10px;
  height: 10px;
  outline: 1px black solid;
}
@for $i from 1 through 20 {
  .area:nth-child(#{21-$i}) {
    background-color: lighten($base-color, $i * 5%);
  }
}
</style>
