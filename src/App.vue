<template>
  <div id="app">
    <!-- <Map/> -->
    <MainPage/>
  </div>
</template>

<script>
// import Map from './components/Map.vue'
import MainPage from './mainPage.vue'


export default {
  name: 'app',
  components: {
    // Map,
    MainPage
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #000000;
  height: 100vh;
}
</style>
