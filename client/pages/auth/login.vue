<template>
  <div>
    <form @submit.prevent="submitForm">
      <div>
        <label>Email</label>
        <input type="text" v-model="login.email" />
      </div>
      <div>
        <label>Password</label>
        <input type="password" v-model="login.password" />
      </div>
      <div>
        <button type="submit">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {

  middleware: ['auth'],
  auth: 'guest',
  
  data() {
    return {
      login: {
        email: '',
        password: ''
      }
    }
  },
  methods: {
    async submitForm() {
      try {
        let response = await this.$auth.loginWith('local', { data: this.login })
        this.$router.replace({name: 'auth-user'})
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>