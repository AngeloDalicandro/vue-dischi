<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <AppHeader />

    <AppBody />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import AppHeader from './components/AppHeader.vue';
import AppBody from './components/AppBody.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
    AppHeader,
    AppBody
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
