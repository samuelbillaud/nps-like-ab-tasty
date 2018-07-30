<template>
  <div class="input-radio">
    <input
      type="radio"
      :name="name"
      :id="id"
      :value="value"
      @change="updateValue($event.target.value)">
      <label :for="id">
        {{ id }}
      </label>
  </div>
</template>

<script>
export default {
  name: 'InputRadio',
  props: {
    name: {
      type: String,
      default: ''
    },
    value: {
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
