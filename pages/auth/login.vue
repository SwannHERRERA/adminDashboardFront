<template>
  <main>
    <h1 class="text-4xl mb-4 text-center">Login</h1>
    <form action method="post">
      <div
        v-show="display_message"
        class="bg-teal-100 border-t-4 border-teal-500 rounded-b text-teal-900 px-4 py-3 shadow-md"
        role="alert"
      >
        <div class="flex">
          <div class="py-1">
            <svg
              class="fill-current h-6 w-6 text-teal-500 mr-4"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 20 20"
            >
              <path
                d="M2.93 17.07A10 10 0 1 1 17.07 2.93 10 10 0 0 1 2.93 17.07zm12.73-1.41A8 8 0 1 0 4.34 4.34a8 8 0 0 0 11.32 11.32zM9 11V9h2v6H9v-4zm0-6h2v2H9V5z"
              />
            </svg>
          </div>
          <div>
            <p class="font-bold">{{ message }}</p>
            <p class="text-sm">
              Make sure you have filled in the form correctly
            </p>
          </div>
        </div>
      </div>
      <myInput
        id="email"
        v-model="email"
        type="email"
        text="Email"
        placeholder="Email"
      />
      <myInput
        id="password"
        v-model="password"
        type="password"
        text="password"
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
import axios from 'axios'
import myInput from '@/components/myInput.vue'

const Cookie = process.client ? require('js-cookie') : undefined

export default {
  middleware: 'notAuthenticated',
  layout: 'auth',
  components: {
    myInput
  },
  data: () => {
    return {
      email: '',
      password: '',
      display_message: false,
      message: ''
    }
  },
  methods: {
    postLogin() {
      return axios({
        method: 'post',
        url: 'http://localhost:8003/admins/login',
        data: {
          email: this.email,
          password: this.password
        },
        headers: {
          'Content-Type': 'application/json'
        }
      }).then((response) => {
        if (response.data.error) {
          this.display_message = true
          this.message = 'message'
        } else {
          const auth = {
            accessToken: response.data.token
          }
          this.$store.commit('setAuth', auth) // mutating to store for client rendering
          Cookie.set('auth', auth) // saving token in cookie for server rendering
          this.$router.push('/admin')
        }
      })
    }
  }
}
</script>
