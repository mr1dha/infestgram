<template>
<div class="container auth-container">
    <div class="row">
        <div class="col-md-4 login text-center">
            <router-link to="/">
                <img src="../assets/brand.png">
            </router-link>
            <br>
            <form @submit.prevent="submitForm()">
                <div class="mb-3">
                <input v-model="email" name="email" type="email" class="form-control" placeholder="Alamat EMail">
            </div>
            <div class="mb-3">
                <input v-model="password" type="password" class="form-control" placeholder="Password">
            </div>
            <button type="submit" class="btn btn-primary w-100 mb-4">MASUK</button>
            </form>
            <span>Belum punya akun? <router-link to="/register">Daftar!</router-link></span>
        </div>
    </div>
</div>
</template>

<script>
import axios from "axios";

export default {
  name: "Login",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    submitForm() {
      const data = {
        email: this.email,
        password: this.password,
      };
      axios
        .post("login", data)
        .then((response) => {
          if (response.status == 200) {
            this.$store.commit("login");
            this.$router.push("/");
          }
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>