<template>
  <div>
    <form @submit.prevent="registerUser">
      <label for="name">Name:</label>
      <input v-model="name" type="text" name="name" value />

      <label for="email">Email:</label>
      <input v-model="email" type="email" name="email" value />
      <p>{{errors.email}}</p>

      <label for="password">Password:</label>
      <input v-model="password" type="password" name="password" value />
      <p>{{errors.password}}</p>

      <button type="submit" name="button">Register</button>

      <router-link to="/login">already have an account? login now</router-link>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      password: '',
      errors: {}
    }
  },
  methods: {
    registerUser() {
      this.$store
        .dispatch('register', {
          name: this.name,
          email: this.email,
          password: this.password
        })
        .then(() => {
          this.$router.push('/dashboard')
        })
        .catch(err => {
          this.errors = err.response.data.errors
        })
    }
  }
}
</script>

<style>
</style>