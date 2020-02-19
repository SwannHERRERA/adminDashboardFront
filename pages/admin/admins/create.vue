<template>
  <div class="w-1/2 mx-auto">
    <h1 class="text-4xl">Create admins</h1>
    <ValidationProvider v-slot="{ errors }" rules="required">
      <myInput
        id="email"
        v-model="email"
        type="email"
        text="email"
        placeholder="exemple@devloup.dev"
      />
      <p v-if="errors">{{ errors[0] }}</p>
    </ValidationProvider>
    <ValidationProvider v-slot="{ errors }" rules="required">
      <myInput
        id="name"
        v-model="name"
        type="text"
        text="full name"
        placeholder="Swann HERRERA"
      />
      <p v-if="errors">{{ errors[0] }}</p>
    </ValidationProvider>
    <ValidationProvider v-slot="{ errors }" rules="required">
      <myInput
        id="password"
        v-model="password"
        type="password"
        text="password"
        name="name"
        placeholder="********"
      />
      <p v-if="errors">{{ errors[0] }}</p>
    </ValidationProvider>
    <p class="text-blue-500 text-xs italic">min lenght 7 chars</p>
    <div class="text-center">
      <button
        class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
        type="button"
        @click="submit"
      >
        Envoyer
      </button>
    </div>
  </div>
</template>

<script>
import { ValidationProvider } from 'vee-validate/dist/vee-validate.full.esm'
import myInput from '@/components/myInput.vue'

export default {
  middleware: 'authenticated',
  components: {
    myInput,
    ValidationProvider
  },
  data: () => {
    return {
      email: '',
      name: '',
      password: ''
    }
  },
  methods: {
    clearInput() {
      this.email = ''
      this.name = ''
      this.password = ''
    },
    async submit() {
      this.$axios.setToken(this.$store.state.auth.accessToken, 'Bearer')
      const result = await this.$axios.$post('/api/admins', {
        email: this.email,
        password: this.password,
        name: this.name
      })
      if (result) {
        this.clearInput()
      }
    }
  }
}
</script>
