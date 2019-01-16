<template>
  <nav class="navbar has-background-transparent" role="navigation" aria-label="main navigation" style="padding: 3rem">
    <div class="navbar-brand">
      <a class="navbar-item" href="https://bulma.io">
        <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28">
      </a>
      <a role="button"
      class="navbar-burger burger"
      :class="[showMenu ? 'is-active' : '']"
      aria-label="menu"
      aria-expanded="false"
      data-target="navbarObjects"
      @click="showMenu = !showMenu;">
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div id="navbarObjects" class="navbar-menu" :class="[showMenu ? 'is-active' : '']">
      <div class="navbar-start">
        <router-link v-for="navItem in navItems" :key="navItem.to" :to="navItem.to" class="navbar-item" style="padding: 16px;">
          {{navItem.name}}
        </router-link>
      </div>
      <div class="navbar-end">
        <div class="navbar-item no-hover">
          <div class="buttons">
            <a class="button is-primary is-outlined" @click="showModal('login')">
              Members Login
            </a>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
import {EventBus} from '@/event-bus.js'

export default {
  components: {
  },
  data: function(){
    return {
      showMenu: false,
      modalComponent: "",
      navItems: [
        {
          // TODO: Create Projects page
          name: "Projects",
          to: "/projects"
        },
      ],
    }
  },
  methods: {
    showModal(component){
      EventBus.$emit('create-modal', component);
    }
  },
}
</script>

<style>
.navbar-item:not(.no-hover):hover {
  background-color: #cfefe6 !important;
  color: #10b285 !important;
}
</style>
