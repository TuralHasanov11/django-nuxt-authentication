<template>
  <div>
    <div v-if="isAuthenticated">
      {{ user?.username }}
      {{ user?.email }}
      <button type="button" class="btn btn-danger" @click="logout">Logout</button> 
      <NuxtLink :to="{name: 'index'}">Back to Home</NuxtLink>   
    </div>
  </div>
</template>

<script>
export default {
  middleware: 'auth',

  computed:{
    isAuthenticated(){
      return this.$auth.loggedIn
    },

    user(){
      return this.$auth.user
    }
  },

  methods:{
    async logout(){
      try {
        let response = await this.$auth.logout()
        this.$router.replace({name: 'auth-login'})
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>