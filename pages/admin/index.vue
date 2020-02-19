<template>
  <div>
    <div v-if="$store.state.auth">
      <p>You are on the Admin page</p>
    </div>
    <p v-else>
      Please
      <button @click="logout">logout</button>.
    </p>
  </div>
</template>

<script>
const Cookie = process.client ? require('js-cookie') : undefined

export default {
  middleware: 'authenticated',
  methods: {
    logout() {
      Cookie.remove('auth')
      this.$store.commit('setAuth', null)
    }
  }
}
</script>
