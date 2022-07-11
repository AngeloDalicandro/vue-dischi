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
@import './styles/common.scss';
</style>
