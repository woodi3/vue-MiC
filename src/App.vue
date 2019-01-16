<template>
  <div id="app">
    <navbar></navbar>
    <router-view/>
    <!-- This mini modal component (could be its own file) will be where we load any of our modal components -->
    <!-- With BulmaCSS all we need to do is toggle the 'is-active' css class to make the modal appear -->
    <div class="modal" :class="[showModal ? 'is-active': '']">
      <div class="modal-background"></div>
      <component :is="modalComponent" @close="showModal = false; modalComponent=''"></component>
    </div>
  </div>
</template>
<script>
import Navbar from './components/Navbar.vue'
import {EventBus} from './event-bus.js'
export default {
  components: {
    "navbar": Navbar,
    "login": () => import('./components/Login.vue'),
    "register": () => import('./components/Register.vue'),
    "new-sponsor": () => import('./components/NewSponsor.vue'),
  },
  data: function(){
    return {
      showModal: false,
      modalComponent: "",
    }
  },
  mounted() {
    //Listen for any create-modal events
    EventBus.$on('create-modal', (component) => {
      //probably don't need this if statement
      if(this.showModal){
        this.modalComponent = "";
        this.showModal = false;
      }
      this.modalComponent = component;
      this.showModal = true;
    })
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
