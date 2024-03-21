<template>
  <div>
    <h1>User login</h1>
    <form @submit.prevent="login">
        <div class="mb-3">
        <label for="username" class="form-label">Username</label>
        <input type="text" class="form-control" id="username" name="username" v-model="form.username" required>
        </div>
        <div class="mb-3">
        <label for="password" class="form-label">Password</label>
        <input type="password" class="form-control" id="password" name="password" v-model="form.password" required>
        </div>
        <button type="submit" class="btn btn-primary">Login</button>
    </form>
  </div>
    
</template>

<script>
import axios from 'axios'
import { jwtDecode } from 'jwt-decode'
export default {
    name: 'LoginComponent',
    data() {
        return {
            form: {
                username: '',
                password: ''
            }
        }
    },
    methods: {
        login() {
            axios.post('http://localhost:8080/auth/generateToken', this.form)
            .then(response => {
                let decode = jwtDecode(response.data);
                localStorage.setItem('token', response.data);
                console.log(decode);
            })
            .catch(error => {
                console.log(error);
            })
        }
    }

}
</script>

<style>

</style>