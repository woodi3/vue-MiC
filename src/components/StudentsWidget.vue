<template>
  <section class="section" style="padding: 2rem">
    <h3 class="title is-2 has-text-left">
      Students
    </h3>
    <p class="title is-size-5 has-text-left has-text-weight-bold" style="margin: 1rem 0;">Have access to</p>
    <div class="columns is-multiline">
      <div class="column is-full" v-for="card in cards" :key="card.text">
        <div class="card" style="background-color: #f5fbf9;">
          <div class="card-content">
            <div class="columns">
              <div class="column is-one-fifth is-vcentered">
                <!-- icon -->
                <span class="icon is-large">
                  <i :class="card.icon"></i>
                </span>
              </div>
              <div class="column is-four-fifth">
                <!-- text -->
                <p class="title is-4">{{card.text}}</p>
                <p class="subtitle is-6">{{card.subText}}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  data: function(){
    return {
      cards: [
        {
          icon: ["fas", "fa-tasks", "fa-3x"],
          text: "Assignment pool",
          subText: "Already completed assignments to guide students"
        },
        {
          icon: ["fas", "fa-network-wired", "fa-3x"],
          text: "Network",
          subText:"An intensive network made from alumna, faculty, and companies"
        },
        {
          icon: ["fas", "fa-user-friends", "fa-3x"],
          text: "Social Circles",
          subText: "Meet others, engage in events, and develop lasting relationships"
        }
      ]
    }
  }
}
</script>
<style>
.is-extra-large {
  height: 5rem;
  width: 5rem;
}
</style>
