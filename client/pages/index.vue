<template>
  <div>
    <h1>Welcome</h1>
    <NuxtLink :to="{name: 'auth-register'}">Register</NuxtLink>
    <NuxtLink :to="{name: 'auth-login'}">Login</NuxtLink>
  </div>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
