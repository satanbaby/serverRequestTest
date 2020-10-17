<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <h1 class="title">多 request 測試器</h1>
  <InputUrl />
  <div id="dashbord">
    <HelloWorld v-for="(url) in urls" :key="url" :sendUri="url" />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import InputUrl from './components/InputUrl.vue'

export default {
  name: 'App',
  data () {
    return {
      urls: ['default_url']
    }
  },
  components: {
    HelloWorld,
    InputUrl
  }
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  // outline: 2px black solid;
}
html,
body {
  height: 100%;
  background-color: mediumaquamarine;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.title{
  margin-bottom: 30px;
}
#dashbord {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #2c3e50;
  height: 100%;
}
</style>
