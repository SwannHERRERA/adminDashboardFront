<template>
  <div>
    <dl-input id="test" design="underline" placeholder="placeholder" />
    <dl-button id="" color="teal">Test button</dl-button>
  </div>
</template>

<script>
import dlInput from '@/components/atoms/dlInput.vue'
import dlButton from '@/components/atoms/dlButton.vue'
export default {
  components: {
    'dl-input': dlInput,
    'dl-button': dlButton
  }
}
</script>
