<template>
  <div class="bg-indigo-100 w-full flex flex-row flex-wrap h-screen">
    <sidebar />
    <nuxt />
  </div>
</template>
<script>
import sidebar from '@/components/organisms/sidebar'
export default {
  component: {
    sidebar
  }
}
</script>
