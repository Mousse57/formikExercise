<template>
      <input :name="name" :type="as" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)" />
</template>

<script>

export default {
  name: 'FieldInput',
  props: {
    as: {
      type: String,
      default: 'text',
    },
    name: {
      type: String,
      default: '',
    },
    modelValue: {
      type: String,
      default: '',
    },
  }
}
</script>
<style scoped>
input {
  border-radius: 5px;
}
</style>