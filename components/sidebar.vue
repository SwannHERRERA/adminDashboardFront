<template>
  <div class="w-1/4 lg:w-1/5">
    <div
      class="bg-white shadow-lg border-t-4 border-indigo-500 absolute bottom-0 w-full md:w-0 md:hidden flex flex-row flex-wrap"
    >
      <div class="w-full text-right">
        <button class="p-2 fa fa-bars text-4xl text-gray-600"></button>
      </div>
    </div>

    <div
      class="w-0 md:w-full h-0 md:h-screen overflow-y-hidden bg-white shadow-lg"
    >
      <div
        class="w-full h-screen antialiased flex flex-col hover:cursor-pointer"
      >
        <a
          class="hover:bg-gray-300 bg-gray-200 border-t-2 p-3 w-full text-xl text-left text-gray-600 font-semibold"
          href=""
          ><i
            class="fa fa-comment text-gray-600 text-2xl pr-1 pt-1 float-right"
          ></i
          >Messages</a
        >
        <a
          class="hover:bg-gray-300 bg-gray-200 border-t-2 p-3 w-full text-xl text-left text-gray-600 font-semibold"
          href=""
          ><i class="fa fa-cog text-gray-600 text-2xl pr-1 pt-1 float-right"></i
          >Settings</a
        >
        <button
          class="hover:bg-gray-300 bg-gray-200 border-t-2 p-3 w-full text-xl text-left text-gray-600 font-semibold"
          @click="logout"
        >
          <i
            class="fa fa-arrow-left text-gray-600 text-2xl pr-1 pt-1 float-right"
          ></i
          >Log out
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
const Cookie = process.client ? require('js-cookie') : undefined

export default {
  middleware: 'authenticated',
  methods: {
    logout() {
      Cookie.remove('auth')
      this.$store.commit('setAuth', null)
      axios.post('http://localhost:8003/admins/me/logout')
      this.$router.push('/')
    }
  }
}
</script>
