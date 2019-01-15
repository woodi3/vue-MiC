<template>
  <section class="section">
    <div class="container">
      <div class="columns">
        <div class="column is-half">
          <h1 class="banner-text title is-size-4-mobile has-text-centered">
            Diversity & Tech
          </h1>
        </div>
        <div class="column is-half" style="align-self: center;">
          <p class="title is-5 has-text-grey-light">
            Take full advantage of the opportunities presented to you.
            Discover opportunities you did not know existed.
            Join a network determined to help you.
          </p>
          <!-- create register modal -->
          <a class="button is-primary is-large" style="margin-top: 1rem" @click="showModal('register')">Join us now!</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { EventBus } from '@/event-bus.js'
export default {
  name: 'banner',
  components: {
  },
  methods: {
    showModal(component){
      EventBus.$emit('create-modal', component);
    }
  },
}
</script>

<style>
@media only screen and (min-width: 768px) {
  .banner-text {
    font-size: 6rem !important;
    color: #0ea077 !important;
  }
}

</style>
