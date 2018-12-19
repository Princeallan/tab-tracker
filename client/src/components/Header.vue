<template>
  <v-toolbar fixed color="cyan" dark>
    <v-toolbar-title class="white--text mr-4">
      <span class="home" @click="navigateTo({name: 'root'})">
        Tab Tracker
      </span>
    </v-toolbar-title>

    <v-toolbar-items>
      <v-btn flat dark>Browse</v-btn>
    </v-toolbar-items>

    <v-spacer></v-spacer>

    <v-toolbar-items>
        <v-btn flat dark @click="navigateTo({name: 'register'})">
          SIGN UP
        </v-btn>
    </v-toolbar-items>

  </v-toolbar>
</template>

<script>

export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    }
  }
}

</script>

<style scoped>
  .home {
    cursor: pointer;
  }
  .home:hover {
    color: brown;
  }
</style>
