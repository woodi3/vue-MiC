<template>
  <div class="hero is-medium">
    <div class="hero-body">
      <banner></banner>
    </div>
    <div class="hero">
      <div class="columns is-gapless">
        <div class="column is-half" id="aboutWidget">
          <about-widget></about-widget>
        </div>
        <div class="column is-half" id="studentsWidget">
          <students-widget></students-widget>
        </div>
      </div>
    </div>
    <div class="hero is-small">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">Catch us at an event!</h1>
          <h2 class="subtitle">We participate in many events.
            Join us now to stay in the loop.</h2>
            <!-- TODO create event modal -->
            <button class="button is-rounded is-primary is-large">View Upcoming Events</button>
        </div>
      </div>
    </div>
    <team-widget></team-widget>
    <div class="hero is-small" style="background-color: #0ea077">
      <div class="hero-body">
        <div class="container">
          <h1 class="title has-text-white-bis">Become a sponsor!</h1>
          <h2 class="subtitle has-text-white-ter">Help us, help others. Get your brand in the community.</h2>
            <!-- TODO create sponsor page or modal -->
            <button class="button is-rounded is-primary is-large">Become Sponsor</button>
        </div>
      </div>
    </div>
    <footer class="footer" style="background-color: #0c8362">
    </footer>
  </div>
</template>

<script>
import Banner from '@/components/Banner.vue'
import About from '@/components/About.vue'
import StudentsWidget from '@/components/StudentsWidget.vue'
import TeamWidget from '@/components/TeamWidget.vue'
export default {
  name: 'home',
  components: {
    "banner": Banner,
    "about-widget": About,
    "students-widget": StudentsWidget,
    "team-widget": TeamWidget,
  },
}
</script>

<style>
#aboutWidget {
  background-color: #b7e7da !important;
}
#studentsWidget {
  background-color: #87d8c2 !important;
}

</style>
