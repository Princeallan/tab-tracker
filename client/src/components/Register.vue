<template>
  <div>
    <h1>Register</h1>
    <input
    type="text"
    name="email"
    v-model="email"
    >
    <br>
    <input
    type="password"
    name="password"
    v-model="password"
    ><br>
    <dir class="error" v-html="error"></dir>
    <br>
    <button @click="register">Register</button>
  </div>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async register () {
      try {
        await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<style>

  .error {
    color: red;
  }

</style>
