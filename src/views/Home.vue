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
    <team-widget></team-widget>
    <event-widget></event-widget>
    <sponsor-widget></sponsor-widget>
    <footer class="footer" style="background-color: #0c8362">
      <h6 class="has-text-grey-lighter" style="padding-top: 2rem;">
        <i class="far fa-copyright"></i>
        Minorities in Computing, Non-profit Org. 2016-present. 
      </h6>
    </footer>
  </div>
</template>

<script>
import Banner from '@/components/Banner.vue'
import About from '@/components/About.vue'
import StudentsWidget from '@/components/StudentsWidget.vue'
import TeamWidget from '@/components/TeamWidget.vue'
import Sponsor from '@/components/Sponsor.vue'
import Events from '@/components/Events.vue'
export default {
  name: 'home',
  components: {
    "banner": Banner,
    "about-widget": About,
    "students-widget": StudentsWidget,
    "team-widget": TeamWidget,
    "sponsor-widget": Sponsor,
    "event-widget": Events,
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
