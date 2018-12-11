<template>
  <v-toolbar fixed dark class="cyan">
    <v-toolbar-title class="mr-4">
      <span class="home" v-on:click="navigateTo({name: 'root'})">
        TabTracker
      </span>
    </v-toolbar-title>

    <v-toolbar-items>
      <v-btn
        flat
        dark
        v-on:click="navigateTo({name: 'songs'})">
        Browse
      </v-btn>

    </v-toolbar-items>

    <v-spacer></v-spacer>

    <v-toolbar-items>

      <v-btn
        v-if="!$store.state.isUserLoggedIn"
        flat
        dark
        v-on:click="navigateTo({name: 'register'})">
        Sign Up
      </v-btn>
      <v-btn
        v-if="!$store.state.isUserLoggedIn"
        flat
        dark
        v-on:click="navigateTo({name: 'login'})">
        Login
      </v-btn>
      <v-btn
        v-if="$store.state.isUserLoggedIn"
        flat
        dark
        v-on:click="logout">
        Logout
      </v-btn>
    </v-toolbar-items>
  </v-toolbar>
</template>

<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    },
    logout () {
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      this.$router.push({
        name: 'root'
      })
    }
  }
}
</script>

<style scoped>
.home {
  cursor: pointer;
}
.home:hover {
  background-color: rgb(0, 233, 233);
}
</style>
