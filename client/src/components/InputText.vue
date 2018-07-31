<template>
  <div class="input-text">
    <textarea
      :name="name"
      :id="id"
      :value="value"
      :placeholder="placeholder"
      @input="updateValue($event.target.value)">
    </textarea>
  </div>
</template>

<script>
export default {
  name: 'InputText',
  props: {
    name: {
      type: String,
      default: ''
    },
    value: {
      type: String,
      default: ''
    },
    placeholder: {
      type: String,
      default: ''
    },
    id: {
      type: String,
      default: ''
    }
  },
  methods: {
    updateValue (value) {
      this.$emit('input', value)
    }
  }
}
</script>
<style scoped>
    textarea {
        display: block;
        margin: auto;
        width: 300px;
        min-height: 100px;
    }
</style>
