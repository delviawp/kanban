<template>
  <div class="container">
    <div class="row content">
      <div class="col-md-6 mb-3">
        <img src="/img.svg" class="img-fluid" alt="image" />
      </div>
      <div class="col-md-6 mb-3">
        <h3 class="signin-text mb-3">Sign In</h3>
        <form @submit.prevent="login">
          <div class="form-group">
            <label for="email">Email</label>
            <input v-model="email" type="email" name="email" class="form-control" />
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input v-model="password" type="password" name="password" class="form-control" />
          </div>
          <button class="btn btn-primary">Sign In</button>
          <p
            role="button"
            @click.prevent="$emit('changePage','register-page')"
          >Don't have any account yet?</p>
        </form>
        <button v-google-signin-button="clientId" class="google-signin-button"> Continue with Google</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "LoginPage",
  data() {
    return {
      email: "",
      password: "",
      clientId : '645674868541-6vv79eleg938e6i99t9idd1vpr0r3flj.apps.googleusercontent.com'
    };
  },
  methods: {
    login() {
      let payload = {
        email: this.email,
        password: this.password
      };
      //console.log(payload)
      this.$emit("login", payload);
    },
    OnGoogleAuthSuccess (idToken) {
      console.log(idToken, 'ini token')
      // Receive the idToken and make your magic with the backend
    },
    OnGoogleAuthFail (error) {
      console.log(error, 'ini eror')
    }
  }
};
</script>

<style>
.google-signin-button {
  color: white;
  background-color: red;
  height: 50px;
  font-size: 16px;
  border-radius: 10px;
  padding: 10px 20px 25px 20px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
</style>