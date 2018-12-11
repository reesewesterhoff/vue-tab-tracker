<template>
  <v-layout column>
    <v-flex>
      <panel-component title="Register">
        <form
          name="tab-tracker-form"
          autocomplete="off"
        >
          <v-text-field
              type="text"
              name="email"
              v-model="email"
              label="Email"
            ></v-text-field>
          <br />
          <v-text-field
              type="password"
              name="password"
              v-model="password"
              label="Password"
              autocomplete="new-passoword"
            ></v-text-field>
          <br />
          <div class="error" v-html="error"></div>
          <v-btn dark class="cyan" v-on:click="register">Register</v-btn>
        </form>
      </panel-component>
    </v-flex>
  </v-layout>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
import Panel from '@/components/Panel'

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
        const response = await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
        this.$store.dispatch('setToken', response.data.token)
        this.$store.dispatch('setUser', response.data.user)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  },
  components: {
    'panel-component': Panel
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  color: red;
}
</style>
