<template>
  <button :class="buttonClass" type="button" @click="$emit('click')">
    <slot></slot>
  </button>
</template>
<script>
export default {
  props: {
    id: {
      type: String,
      require: false,
      default: ''
    },
    type: {
      type: String,
      required: false,
      default: 'button'
    },
    design: {
      type: String,
      required: false,
      default: 'outline'
    },
    color: {
      type: String,
      required: false,
      default: 'blue'
    }
  },
  computed: {
    buttonClass() {
      switch (this.design) {
        case 'outline':
          return `bg-transparent hover:bg-${this.color}-500 text-${this.color}-700 font-semibold hover:text-white py-2 px-4 border border-${this.color}-500 hover:border-transparent rounded`

        default:
          return ''
      }
    }
  }
}
</script>
