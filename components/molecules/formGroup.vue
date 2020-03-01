<template>
  <div>
    <label class="block text-gray-700 text-sm font-bold mb-2" :for="id"
      ><slot></slot
    ></label>
    <dl-input :id="id" :type="type" :value="value" :placeholder="placeholder" />
  </div>
</template>

<script>
import dlInput from '@/components/atoms/dlInput.vue'
export default {
  components: {
    'dl-input': dlInput
  },
  props: {
    id: {
      type: String,
      required: true
    },
    type: {
      type: String,
      required: false,
      default: 'text'
    },
    name: {
      type: String,
      required: false,
      default: ''
    },
    placeholder: {
      type: String,
      required: false,
      default: ''
    },
    value: {
      type: String,
      required: false,
      default: ''
    },
    design: {
      type: String,
      required: false,
      default: 'classic'
    }
  }
}
</script>
