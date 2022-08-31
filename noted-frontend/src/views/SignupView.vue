<script>
import axios from "axios";

export default {
  data: function () {
    return {
      newUserParams: {},
      errors: [],
    };
  },
  methods: {
    submit: function () {
      axios
        .post("/users", this.newUserParams)
        .then((response) => {
          console.log(response.data);
          this.$router.push("/login");
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>

<template>
  <div class="signup">
    <form v-on:submit.prevent="submit()">
      <h1>Sign Up</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <div class="Name">
        <label>UserName:</label>
        <input
          type="text"
          class="form-control"
          id="Name"
          placeholder="Put in your username"
          v-model="newUserParams.name"
        />
      </div>
      <div>
        <label for="Emailt" class="form-label">Email:</label>
        <input
          type="email"
          class="form-control"
          id="formGroupExampleInput"
          placeholder="Please put in your email"
          v-model="newUserParams.email"
        />
      </div>
      <div>
        <label>Password:</label>
        <input
          type="password"
          class="form-control"
          id="formGroupExampleInput"
          placeholder="Think of a great and unique password!"
          v-model="newUserParams.password"
        />
      </div>
      <button
        class="btn btn-outline-primary"
        style="
          --bs-btn-padding-y: 0.25rem;
          --bs-btn-padding-x: 0.5rem;
          --bs-btn-font-size: 1.5rem;
          margin-top: 20px;
        "
        type="submit"
        value="Submit"
      >
        Submit
      </button>
    </form>
  </div>
</template>
<style>
.signup {
  font-size: medium;
  font-style: normal;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  width: 50%;
  text-align: center;
  align-content: center;
  margin: auto;
  padding: 20px;
}
</style>
