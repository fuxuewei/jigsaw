<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Onebox/>
  </div>
</template>

<script>
import Onebox from './components/Onebox.vue'

export default {
  name: 'app',
  components: {
    Onebox
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
