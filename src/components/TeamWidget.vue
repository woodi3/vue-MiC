<template>
  <div class="hero is-small" style="background-color: #0c8362">
    <div class="hero-body">
      <div class="container">
        <h1 class="title has-text-white-ter">Meet the board!</h1>
        <h2 class="subtitle has-text-white-ter">The board works diligently to give our members the best service and value.</h2>
        <div class="columns">
          <div class="column is-one-third is-offset-one-third">
            <div class="card">
              <div class="card-image">
                <figure class="image is-4by3">
                  <img :src="president.avatar" alt="member avatar">
                </figure>
              </div>
              <div class="card-content">
                <div class="media">
                  <div class="media-left">
                    <figure class="image is-48x48">
                      <img class="is-rounded" :src="president.avatar" alt="smaller member avatar">
                    </figure>
                  </div>
                  <div class="media-content">
                    <p class="title is-4">{{president.name}}</p>
                    <p class="subtitle is-6">{{president.position}}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="columns is-multiline">
          <div v-for="member in board" :key="member.position" class="column">
            <div class="card">
              <div class="card-image">
                <figure class="image is-4by3">
                  <img :src="member.avatar" alt="member avatar">
                </figure>
              </div>
              <div class="card-content">
                <div class="media">
                  <div class="media-left">
                    <figure class="image is-48x48">
                      <img class="is-rounded" :src="member.avatar" alt="smaller member avatar">
                    </figure>
                  </div>
                  <div class="media-content">
                    <p class="title is-4">{{member.name}}</p>
                    <p class="subtitle is-6">{{member.position}}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>
<script>
export default {
  data: function(){
    return {
      president: {
          avatar: "https://via.placeholder.com/100",
          name: "Kierra Robinson",
          position: "President",
          isPres: true,
      },
      board: [
        {
          avatar: "https://via.placeholder.com/100",
          name: "Kristina Matthews",
          position: "Vice-President",
        },
        {
          avatar: "https://via.placeholder.com/100",
          name: "Tiana Sullivan",
          position: "Treasurer",
        },
        {
          avatar: "https://via.placeholder.com/100",
          name: "Jared Davis",
          position: "Secretary",
        },
        {
          avatar: "https://via.placeholder.com/100",
          name: "Marquis Wideman",
          position: "Social Media Coordinator",
        }
      ]
    }
  }
}
</script>
<style></style>
