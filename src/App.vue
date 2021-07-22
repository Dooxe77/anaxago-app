<template>
  <div id="app">
    <Header />
    <Home />
  </div>
</template>

<script>
import Home from './components/pages/Home.vue'
import Header from './components/layout/Header.vue'

export default {
  name: 'App',
  components: {
    Header,
    Home, 
  }
}
</script>

<style lang="scss">
@import "./styles/index.scss";

body {
  margin: 0;
  font-family: ProximaNova,Arial,sans-serif;
  -webkit-font-smoothing: antialiased;
}

</style>
