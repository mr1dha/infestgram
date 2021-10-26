<template>
    <div class="container auth-container">
        <div class="row">
            <div class="col-md-4 login text-center">
            <router-link to="/">
                <img src="../assets/brand.png">
            </router-link>
                <h6 class="my-3"><b>Buat akun baru</b></h6>
                <form @submit.prevent="submitForm()">
                    <div class="mb-3">
                        <input v-model="name" type="text" class="form-control" placeholder="Nama Lengkap">
                    </div>
                    <div class="mb-3">
                    <input v-model="email" type="email" class="form-control" placeholder="Alamat EMail">
                </div>
                <div class="mb-3">
                    <input v-model="password" type="password" class="form-control" placeholder="Masukkan Password">
                </div>
                <div class="mb-3">
                    <input v-model="password_confirmation" type="password" class="form-control" placeholder="Ulangi Password">
                </div>
                <button type="submit" class="btn btn-primary w-100 mb-4">DAFTAR</button>
                </form>
                <span>Sudah punya akun? <router-link to="/login">Masuk!</router-link></span>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Rwgister',
    data() {
        return { 
            name : '',
            email : '',
            password : '',
            password_confirmation : ''
        }
    },
    methods: {
        submitForm() {
            const data = {
                name : this.name,
                email : this.email,
                password : this.password,
                password_confirmation : this.password_confirmation
            }
            axios.post('register', data)
                .then(response => {
                    if (response.status == 201)
                        this.$router.push('/login');
                })
                .catch(err => console.log(err.response.data));
        }
    }
}
</script>

<style>
.auth-container, .auth-container .row {
    height: 100vh;
}
 
.auth-container .row {
    align-items: center;
    justify-content: center;
}
.auth-container .login {
    padding: 2em;
    background: white;
    border-radius: 15px;
}
 
.login img {
    display: block;
    margin: auto;
    width: 40%;
}
</style>