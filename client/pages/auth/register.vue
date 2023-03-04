<template>
  <div>
    <form @submit.prevent="submitForm">
      <div>
        <label>Username</label>
        <input type="text" v-model="register.username" />
      </div>
      <div>
        <label>Email</label>
        <input type="text" v-model="register.email" />
      </div>
      <div>
        <label>Password</label>
        <input type="password" v-model="register.password" />
      </div>
      <div>
        <label>Confirm Password</label>
        <input type="password" v-model="register.password2" />
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
      register: {
        username: '',
        email: '',
        password: '',
        password2: ''
      }
    }
  },
  methods: {
    async submitForm() {
      try {
        let response = await this.$axios.$post('auth/register', this.register)
        this.$router.replace({name: 'auth-login'})
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>