<template>
    <div class="container">
         <div class="col-md-6 m-auto">
            <h1>Login Page</h1>
        <div class="mt-3">
            <form @submit.prevent="submitLogin">
            <div class="mb-3">
                <label for="exampleFormControlInput1" class="form-label">Email</label>
                <input type="email" class="form-control" id="exampleFormControlInput1" placeholder="name@example.com" v-model="form.email">
            </div>
            <div class="mb-3">
                <label for="exampleFormControlInput1" class="form-label">Password</label>
                <input type="password" class="form-control" id="exampleFormControlInput1" v-model="form.password">
            </div>
            <div>
                <button type="submit" class="btn btn-primary">Login</button>
            </div>
        </form>

        </div>
         </div>

    </div>
</template>
<script setup>
import {ref } from 'vue';
import axios from 'axios'

import { useRouter } from 'vue-router'

const router = useRouter();

const form = ref({
    email: '',
    password: ''
});


const submitLogin = async () => {
    await axios.post('/login',{
        email: form.value.email,
        password: form.value.password

    });

    router.push('/');
}
/*
const csrfToken = document.head.querySelector('meta[name="csrf-token"]').content;

const submitLogin = async () => {
    await axios.post('/login', {
        email: form.value.email,
        password: form.value.password
    }, {
        headers: {
            'X-CSRF-TOKEN': csrfToken,
            'Content-Type': 'application/json'
        }
    });

    router.push('/');
}*/


</script>
