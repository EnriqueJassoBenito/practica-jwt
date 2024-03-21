<template>
  <div>
    <h1>HOLA</h1>
    <b-row>
        <b-col>
            <user-login-vue/>
        </b-col>
        <b-col>
            <user-registration-vue/>
        </b-col>
    </b-row>
    <UserAuthVue/>
  </div>
</template>

<script>
import UserLoginVue from './UserLogin.vue'
import UserRegistrationVue from './UserRegistration.vue'
import UserAuthVue from './UserAuth.vue'
export default {
    components: {
        UserRegistrationVue,
        UserLoginVue,
        UserAuthVue
    }
}

</script>

<style>

</style>