<template>
  <div class="modal-card">
    <header class="modal-card-head">
      <p class="modal-card-title">Member Registration</p>
      <button class="delete" aria-label="close" @click="$emit('close')"></button>
    </header>
    <section class="modal-card-body">
      <div class="field">
        <div class="control is-medium has-icons-left has-icons-right"
          :class="[emailLoader ? 'is-loading' : '']">
          <input class="input is-medium"
            :class="[emailValid ? '' : 'is-danger']"
            type="text"
            required
            placeholder="Email address"
            v-model.trim="user.email">
          <span class="icon is-small is-left">
            <i class="fas fa-user"></i>
          </span>
          <span class="icon is-small is-right has-text-success" v-if="emailValid">
            <i class="fas fa-check"></i>
          </span>
          <p class="help is-danger">{{emailValid ? "" : "Please enter a valid email address"}}</p>
        </div>
      </div>
      <div class="field">
        <div class="control is-medium has-icons-left has-icons-right"
          :class="[passLoader ? 'is-loading' : '']">
          <input class="input is-medium" :class="[passValid ? '':'is-danger']" type="password" required placeholder="Password"
          v-model="user.password">
          <span class="icon is-small is-left">
            <i class="fas fa-lock"></i>
          </span>
          <span class="icon is-small is-right has-text-success" v-if="passValid">
            <i class="fas fa-check"></i>
          </span>
          <p class="help is-danger">{{passValid ? "" : "Password must be at least 6 characters long and contain at least 1 letter"}}</p>
        </div>
      </div>
      <div class="field" v-if="passValid">
        <div class="control is-medium has-icons-left has-icons-right"
          :class="[passLoader ? 'is-loading' : '']">
          <input class="input is-medium" :class="[copyPassValid ? '':'is-danger']" type="password" required placeholder="Password"
          v-model="copyPass">
          <span class="icon is-small is-left">
            <i class="fas fa-lock"></i>
          </span>
          <span class="icon is-small is-right has-text-success" v-if="copyPassValid">
            <i class="fas fa-check"></i>
          </span>
          <p class="help is-danger">{{copyPassValid ? "" : "Passwords do not match!"}}</p>
        </div>
      </div>
    </section>
    <footer class="modal-card-foot">
      <button class="button is-success" :class="[regLoading ? 'is-loading' : '']" :disabled="registerCheck" @click="register">Register</button>
      <button class="button" @click="$emit('close')">Cancel</button>
    </footer>
  </div>
</template>

<script>
export default {
  data: function(){
    return {
      user: {
        email: "",
        password: ""
      },
      copyPass: "",
      emailLoader: false,
      passLoader: false,
      regLoading: false,
    }
  },
  methods: {
    register() { // TODO: make async
      this.regLoading = true;
      setTimeout(() => this.regLoading=false, 1500);
    },
    isEmail(){
      let re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(String(this.user.email).toLowerCase());
    },
    isPass(){
      let re = /^(?=.*[a-z])(?=.{6,})/;
      return re.test(this.user.password);
    }
  },
  computed: {
    registerCheck(){ //TODO check all required inputs
      return !this.emailValid || !this.passValid || !this.copyPassValid;
    },
    emailValid(){
      return this.user.email !=="" && this.isEmail();
    },
    passValid(){
      return this.user.password !== "" && this.isPass();
    },
    copyPassValid(){
      return this.user.password === this.copyPass;
    }
  },
}
</script>

<style></style>
