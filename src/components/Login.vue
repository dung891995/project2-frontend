<template>
  <div>
    <h2>Login</h2>

    <form>
      <div class="form-login">
        <label for="Email" class="form-label-email">Email</label>
        <input type="text" class="form-control" id="inputEmail" placeholder="Email" v-model="email" />

        <label for="Password" class="form-label-password">Password</label>
        <input type="password" class="form-control" id="inputPassword" placeholder="Password" v-model="password" />

        <button type="button" class="btn btn-primary" @click='login'>Sign in</button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      email: "",
      password: ""
    };
  },
  methods: {
    login() {
      axios
        .post("http://localhost:3000/auth/login", {
          email:this.email,
          password: this.password
        })
        .then(function(response) {
          console.log(response);
        })
        .catch(function(error) {
          console.log(error);
        });
    }
  }
};
</script>