<template>
  <div id="app">
    <navbar></navbar>
    <router-view/>
  </div>
</template>
<script>
import Navbar from './components/Navbar.vue'
export default {
  components: {
    "navbar": Navbar,
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css?family=Open+Sans');
#app {
  font-family: 'Open Sans', 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #f5fbf9;
}

.has-background-transparent {
  background-color: transparent !important;
  background-image: none !important;
}

</style>
