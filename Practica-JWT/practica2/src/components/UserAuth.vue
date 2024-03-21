<template>
  <div>
    <b-row>
        <b-button class="col-5 m-3 p-3" @click="consumoAdmin()">ROL ADMIN</b-button>
        <b-button class="col-5 m-3 p-3" @click="consumoUser()">ROL USER</b-button>
    </b-row>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    methods: {
        consumoAdmin() {
            const token = localStorage.getItem('token');
            //validamos si existe token y hacemos la peticion
            if(token) {
                axios.get("http://localhost:8080/auth/admin/adminProfile", {
                    headers: { //configuramos de la peticion donde introducimos el atributo de autorizacion
                        Authorization: `Bearer ${token}`,
                    }, //nosotros tenemos que apuntar al valor de 'Beaner' y concatenar el token
                })
                .then((response)=>{
                    console.log(response);
                })
                .catch((error)=>{
                    console.log(error);
                })
            }
        },
        consumoUser() {
            const token = localStorage.getItem('token');
            if (token) {
                axios.get("http://localhost:8080/auth/user/userProfile", {
                    headers: {
                        Authorization: `Bearer ${token}`,
                    },
                })
                .then((response)=>{
                    console.log(response);
                })
                .catch((error)=>{
                    console.log(error);
                })
            }
        }
    }
}
</script>

<style>

</style>