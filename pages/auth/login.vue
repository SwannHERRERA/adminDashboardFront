<template>
  <main>
    <h1 class="text-4xl mb-4 text-center">Login</h1>
    <form action method="post">
      <myInput
        id="username"
        type="text"
        text="Username"
        name="username"
        placeholder="Username"
      />
      <myInput
        id="password"
        type="password"
        text="password"
        name="password"
        placeholder="*******"
      />
      <p class="mb-3">
        <nuxt-link
          to="/auth/new_password"
          class="inline-block align-baseline font-bold text-sm text-blue-300 hover:text-blue-500"
          >Password lost ?</nuxt-link
        >
      </p>
      <p class="text-center mb-4">
        <button
          type="button"
          class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
          @click="postLogin"
        >
          Sign In
        </button>
      </p>
    </form>
  </main>
</template>
<script>
import myInput from '@/components/myInput.vue'

const Cookie = process.client ? require('js-cookie') : undefined

export default {
  middleware: 'notAuthenticated',
  layout: 'auth',
  components: {
    myInput
  },
  methods: {
    postLogin() {
      setTimeout(() => {
        // we simulate the async request with timeout.
        const auth = {
          accessToken: 'someStringGotFromApiServiceWithAjax'
        }
        this.$store.commit('setAuth', auth) // mutating to store for client rendering
        Cookie.set('auth', auth) // saving token in cookie for server rendering
        this.$router.push('/admin')
      }, 1000)
    }
  }
}
</script>
