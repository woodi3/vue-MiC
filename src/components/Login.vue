<template>
  <div class="modal-card">
    <header class="modal-card-head">
      <p class="modal-card-title">Member's Login</p>
      <button class="delete" aria-label="close" @click="$emit('close')"></button>
    </header>
    <section class="modal-card-body">
      <div class="field">
        <div class="control is-medium has-icons-left"
          :class="[loading ? 'is-loading' : '']">
          <input class="input is-medium"
            :class="[valid ? '' : 'is-danger']"
            type="text"
            required
            placeholder="Username or email"
            v-model.trim="user.usernameOrEmail">
          <span class="icon is-small is-left">
            <i class="fas fa-user"></i>
          </span>
          <p class="help is-danger">{{valid ? "" : "Please enter a valid username or email address"}}</p>
        </div>
      </div>
      <div class="field">
        <div class="control is-medium has-icons-left"
          :class="[loading ? 'is-loading' : '']">
          <input class="input is-medium" type="password" required placeholder="Password"
          v-model="user.password">
          <span class="icon is-small is-left">
            <i class="fas fa-lock"></i>
          </span>
          <p class="help is-danger">{{valid ? "" : "Please enter a valid password"}}</p>
        </div>
      </div>
      <div class="field">
        <div class="control">
          <label class="checkbox">
            <input type="checkbox">
            Remember me
          </label>
        </div>
      </div>
    </section>
    <footer class="modal-card-foot">
      <button class="button is-success" :class="[loading ? 'is-loading' : '']" :disabled="loginCheck" @click="login">Login</button>
      <button class="button" @click="$emit('close')">Cancel</button>
    </footer>
  </div>
</template>

<script>
export default {
  data: function(){
    return {
      user: {
        usernameOrEmail: "",
        password: ""
      },
      loading: false,
      valid: true,
    }
  },
  methods: {
    login() { // TODO: make async
      this.loading = true;
      setTimeout(() => {
        this.valid= false;
        this.loading = false;
      }, 1500);
    },
  },
  computed: {
    loginCheck(){
      return this.user.usernameOrEmail === "" || this.user.password ===""
    }
  },
}
</script>

<style></style>
