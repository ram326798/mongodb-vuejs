<template>
  <div class="container">
    <form>
      <div class="well">
        <h4>Login</h4>
        <div class="form-group">
          <label class="pull-left"> Username </label>
          <input
            type="text"
            class="form-control"
            placeholder="Username"
            v-model="User.username"
            required
          />
        </div>
        <div class="form-group">
          <label class="pull-left"> Password </label>
          <input
            type="text"
            class="form-control"
            placeholder="Password "
            v-model="User.password"
            required
          />
        </div>
      </div>
      <button
        type="submit"
        class="btn btn-large btn-block btn-primary full-width"
        @click="addToAPI"
      >
        Signin
      </button>
      <router-link to="/accounts/signup">
        <button
          type="submit"
          class="btn btn-large btn-block btn-primary full-width"
        >
          Signup
        </button>
      </router-link>
    </form>
  </div>
</template>

<script>
/*eslint-disable */
import axios from "axios";
import router from "../router";
export default {
  name: "Login",
  data() {
    return {
      User: {
        // name: "",
        username: "",
        password: "",
      },
    };
  },
  methods: {
    addToAPI() {
      let newUser = {
        // name: this.User.name,
        username: this.User.username,
        password: this.User.password,
      };
      console.log(newUser);
      if (this.newUser != null) {
        axios
          .post("http://127.0.0.1:5000/accounts/login", newUser)

          .then((response) => {
            console.log(response.data);
            router.push({ name: "accountdetails" });
          })
          .catch((error) => {
            console.log(error);
          });
      } else {
        return "Username and password should not blank";
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
