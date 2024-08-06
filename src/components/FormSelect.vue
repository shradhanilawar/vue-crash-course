<template>
  <div class="col">
    <label class="form-label">{{ label }}</label>
    <select class="form-select" :value="modelValue" @change="$emit('update:modelValue', $event.target.value)">
      <option value="" disabled>{{ placeholder }}</option>
      <option v-for="option in options" :key="option.value" :value="option.value">
        {{ option.text }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    label: String,
    modelValue: [String, Number],
    options: Array,
    placeholder: String,
  },
};
</script>
