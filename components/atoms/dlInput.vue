<template>
  <div :class="containerClass">
    <input
      :id="id"
      :class="inputClass"
      :type="type"
      :name="name"
      :placeholder="placeholder"
      :value="value"
      @input="$emit('input', $event.target.value)"
    />
  </div>
</template>

<script>
export default {
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
  },
  computed: {
    inputClass() {
      switch (this.design) {
        case 'underline':
          return 'appearance-none bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none'
        case 'borderless':
          return 'appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500'
        default:
          return 'shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline'
      }
    },
    containerClass() {
      switch (this.design) {
        case 'underline':
          return 'border-b border-b-2 border-teal-500 py-2'
        default:
          return ''
      }
    }
  }
}
</script>
