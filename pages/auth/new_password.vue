<template>
  <main>
    <h1 class="text-4xl mb-4 text-center">Password lost ?</h1>
    <form action method="post">
      <myInput
        id="email"
        type="email"
        text="email"
        name="email"
        placeholder="swann@devloup.dev"
      />
      <p class="flex justify-between mb-4">
        <button
          class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
          type="submit"
        >
          send
        </button>
        <nuxt-link
          to="/auth/login"
          class="bg-transparent hover:bg-gray-500 text-gray-700 font-semibold hover:text-white py-2 px-4 border border-gray-500 hover:border-transparent rounded"
        >
          Back
        </nuxt-link>
      </p>
    </form>
  </main>
</template>
<script>
import myInput from '@/components/myInput.vue'

export default {
  layout: 'auth',
  middleware: 'notAuthenticated',
  components: {
    myInput
  }
}
</script>
