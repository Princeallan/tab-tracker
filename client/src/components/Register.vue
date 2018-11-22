<template>
  <v-container fluid fill-height>
    <v-layout align-center justify-center>
      <v-flex xs12 sm8 md4>
        <v-card class="elevation-12">
          <v-toolbar color="cyan" dark>
            <v-toolbar-title>Register form</v-toolbar-title>
          </v-toolbar>

          <v-card-text>
          <v-text-field
            type="text"
            placeholder="Email"
            name="email"
            v-model="email"> </v-text-field>
            <br>
            <v-text-field
            type="password"
            placeholder="Password"
            name="password"
            v-model="password"> </v-text-field>
            <br>
            <div class="error" v-html="error"></div>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn @click="register" dark class="cyan">Register</v-btn>
        </v-card-actions>

        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
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

<style scoped>

  .error {
    color: red;
    background: white !important;
  }

</style>
