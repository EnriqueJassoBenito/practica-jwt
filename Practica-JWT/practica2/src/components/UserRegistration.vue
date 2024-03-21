<template>
    <div>
        <h1>Iniciar Sesion</h1>
        <form @submit.prevent="registerUser">
        <div class="mb-3">
            <label for="name" class="form-label">Nombre</label>
            <input type="text" class="form-control" id="name" name="name" v-model="form.name" required>
        </div>
        <div class="mb-3">
            <label for="username" class="form-label">Nombre de usuario</label>
            <input type="text" class="form-control" id="username" name="username" v-model="form.username" required>
        </div>
        <div class="mb-3">
            <label for="password" class="form-label">Contraseña</label>
            <input type="password" class="form-control" id="password" name="password" v-model="form.password">
        </div>
        <button type="submit" class="btn btn-primary">Registrar</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    data() {
        return {
            form: {
                name: '',
                username: '',
                password: ''
            }
        }
    },
    methods: {
        registerUser() {
            axios.post('http://localhost:8080/auth/addNewUser', this.form)
            .then(response => {
                console.log("Repuesta del servidor",response);
            });
        }
    }
}
</script>

<style>

</style>