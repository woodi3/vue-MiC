<template>
  <div class="hero is-small" style="background-color: #0ea077">
    <div class="hero-body">
      <div class="container">
        <h1 class="title has-text-white-bis">Become a sponsor!</h1>
        <h2 class="subtitle has-text-white-ter">Help us, help others. Get your brand in the community.</h2>
        <button class="button is-rounded is-primary is-large" @click="showModal('new-sponsor')">Become Sponsor</button>
      </div>
    </div>
  </div>
</template>
<script>
import { EventBus } from '@/event-bus.js'
export default {
  methods: {
    showModal(component) {
      EventBus.$emit('create-modal', component);
    },
  }
}
</script>
<style></style>
