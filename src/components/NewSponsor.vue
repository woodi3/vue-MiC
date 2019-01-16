<template>
  <div class="modal-card">
    <header class="modal-card-head">
      <p class="modal-card-title">Sponsor Registration</p>
      <button class="delete" aria-label="close" @click="$emit('close')"></button>
    </header>
    <section class="modal-card-body">
      <div class="field">
        <div class="control is-medium has-icons-left">
          <input class="input is-medium"
            type="text"
            required
            placeholder="Your name"
            v-model="user.name">
          <span class="icon is-small is-left">
            <i class="fas fa-user"></i>
          </span>
          <p class="help is-danger">{{nameValid ? "" : "Please enter your name"}}</p>
        </div>
      </div>
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
            <i class="fas fa-envelope"></i>
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
          <input class="input is-medium" :class="[copyPassValid ? '':'is-danger']" type="password" required placeholder="Re-enter your password"
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
      <div class="field" v-if="user.isCompany">
        <div class="control is-medium has-icons-left has-icons-right"
          :class="[companyLoader ? 'is-loading' : '']">
          <input class="input is-medium" :class="[companyNameValid ? '':'is-danger']" type="text" required placeholder="Company Name"
          v-model="user.companyName">
          <span class="icon is-small is-left">
            <i class="fas fa-sitemap"></i>
          </span>
          <span class="icon is-small is-right has-text-success" v-if="companyNameValid">
            <i class="fas fa-check"></i>
          </span>
          <p class="help is-danger">{{companyNameValid ? "" : "Enter your company's name"}}</p>
        </div>
      </div>
      <div class="field">
        <label class="checkbox">
          <input type="checkbox" v-model="user.isCompany">
          I am part of an organization
        </label>
      </div>
    </section>
    <footer class="modal-card-foot">
      <button class="button is-success" :class="[regLoading ? 'is-loading' : '']" :disabled="registerCheck" @click="register">Become a Sponsor</button>
      <button class="button" @click="$emit('close')">Cancel</button>
    </footer>
  </div>
</template>

<script>
export default {
  data: function(){
    return {
      user: {
        isCompany: false,
        companyName: "",
        companyAddress: "",
        name: "",
        email: "",
        password: ""
      },
      copyPass: "",
      emailLoader: false,
      passLoader: false,
      regLoading: false,
      companyLoader: false,
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
    },
  },
  computed: {
    registerCheck(){ //TODO check all required inputs
      return !this.emailValid || !this.passValid || !this.copyPassValid || (!this.companyNameValid && this.user.isCompany) || !this.nameValid;
    },
    emailValid(){
      return this.user.email !=="" && this.isEmail();
    },
    passValid(){
      return this.user.password !== "" && this.isPass();
    },
    copyPassValid(){
      return this.user.password === this.copyPass;
    },
    companyNameValid() {
      return this.user.companyName !== "" && this.user.isCompany;
    },
    nameValid(){
      return this.user.name !== "";
    },
  },
}
</script>

<style></style>
