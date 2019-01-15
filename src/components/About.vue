<template>
  <section class="section" style="padding: 2rem">
    <h3 class="title is-2 has-text-left">
      About Us
      <p class="is-size-5" style="margin-top: 1rem;">Since 2016</p>
    </h3>
    <hr id="aboutUsDivider" />
    <div class="columns">
      <div class="column has-text-left">
        <h4 class="title is-3">Our goal</h4>
        <p class="is-size-5">
          Our journey began almost {{activeYears}} years ago with the purpose
          of engaging minorities in the Computing College at the University of South Carolina.
          It would be a place where we could connect the students that were struggling
          and the students that were excelling to prevent discouragement. Taking that a step
          further, we try to connect students and employers to improve hire rates for
          minority students.
        </p>
      </div>
    </div>
  </section>
</template>
<script>
import * as moment from 'moment'

export default {
  data: function(){
    return {
      activeYears: (moment().year() - 2016),
    }
  }
}
</script>
<style>
#aboutUsDivider {
  display: block;
  height: 1px;
  border: 0;
  border-top: 1px solid #0ea077;
  margin: 2em 0;
  padding: 0;
  max-width: 345px;
}
</style>
