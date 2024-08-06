<template>
  <div class="col">
    <label class="form-label">{{ label }}</label>
    <input type="text" class="form-control" :placeholder="placeholder" :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)" />
  </div>
</template>

<script>
export default {
  props: {
    label: String,
    modelValue: String,
    placeholder: String,
  },
};
</script>
