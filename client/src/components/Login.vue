<template>
  <v-layout align-center justify-center>
    <v-flex xs12 sm8 md4>
      <v-card class="elevation-12">
        <v-toolbar color="cyan" dark>
          <v-toolbar-title>Login form</v-toolbar-title>
        </v-toolbar>

        <v-card-text>
          <v-text-field
            type="text"
            placeholder="Email"
            name="email"
            v-model="email"></v-text-field>
          <br>
          <v-text-field
            type="password"
            placeholder="Password"
            name="password"
            v-model="password"></v-text-field>
          <br>
          <div class="error" v-html="error"></div>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn @click="login" dark class="cyan">Login</v-btn>
        </v-card-actions>

      </v-card>
    </v-flex>
  </v-layout>
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
    async login () {
      try {
        const response = await AuthenticationService.login({
          email: this.email,
          password: this.password
        })
        this.$store.dispatch('setToken', response.data.token)
        this.$store.dispatch('setUser', response.data.user)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<style scoped>

  .error {
    color: red;
    background: white !important;
  }

</style>
