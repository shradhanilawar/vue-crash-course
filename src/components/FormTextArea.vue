<template>
  <div class="col">
    <label class="form-label">{{ label }}</label>
    <textarea class="form-control" rows="3" :placeholder="placeholder" v-model="internalValue"
      @input="$emit('update:modelValue', $event.target.value)"></textarea>
  </div>
</template>

<script>
export default {
  props: {
    label: String,
    modelValue: String,
    placeholder: String,
  },
  computed: {
    internalValue: {
      get() {
        return this.modelValue;
      },
      set(value) {
        this.$emit('update:modelValue', value);
      },
    },
  },
};
</script>
