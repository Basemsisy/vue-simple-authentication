<template>
  <div class="home">
    <h1>Welcome to the App!</h1>
    <div v-if="!loggedIn">
      To Use This App You'll Need To
      <router-link to="/login">Login</router-link>&nbsp;or
      <router-link to="/register">Register</router-link>
    </div>
  </div>
</template>

<script>
import authMixin from '../mixins/authUserMixin'

export default {
  mixins: [authMixin]
}
</script>
