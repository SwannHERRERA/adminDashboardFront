<template>
  <div class=" bg-orange-100 rounded card p-6">
    <h1 class="text-2xl mb-2">Connexion</h1>
    <hr class="border-1 mb-3" />
    <form>
      <div class="md:flex md:items-center mt-4 mb-6">
        <div class="md:w-1/3">
          <label
            class="block text-gray-500 font-bold mb-1 md:mb-0 pr-4"
            for="inline-full-name"
          >
            Username :
          </label>
        </div>
        <div class="md:w-2/3">
          <input
            id="username"
            type="text"
            class="bg-orange-200 appearance-none border-2 border-orange-400 rounded w-full"
          />
        </div>
      </div>
      <div class="md:flex md:items-center mt-4 mb-6">
        <div class="md:w-1/3">
          <label
            class="block text-gray-500 font-bold mb-1 md:mb-0 pr-4"
            for="inline-full-name"
          >
            Password :
          </label>
        </div>
        <div class="md:w-2/3">
          <input
            id="password"
            type="password"
            class="bg-orange-200 appearance-none border-2 border-orange-400 rounded w-full"
          />
        </div>
      </div>
      <p class="text-center">
        <button
          type="button"
          class=" bg-orange-400 hover:bg-transparent border hover:border-red-700 text-right font-bold py-2 px-4 rounded"
        >
          Se connecter
        </button>
      </p>
    </form>
  </div>
</template>

<style scoped>
.card {
  width: 400px;
}
</style>

<script>
export default {
  layout: 'auth'
}
</script>
