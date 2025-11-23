<script setup>
defineProps({
  modelValue: String,
  label: String,
  type: {
    type: String,
    default: 'text'
  },
  placeholder: String
});

defineEmits(['update:modelValue']);
</script>

<template>
  <div class="input-wrapper">
    <label v-if="label" class="input-label">{{ label }}</label>
    <input 
      :type="type" 
      :value="modelValue"
      :placeholder="placeholder"
      @input="$emit('update:modelValue', $event.target.value)"
      class="s-input"
    />
  </div>
</template>

<style scoped>
.input-wrapper {
  display: flex;
  flex-direction: column;
  margin-bottom: 16px;
  width: 100%;
}

.input-label {
  font-size: 12px;
  font-weight: 600;
  margin-bottom: 6px;
  color: #555;
}

.s-input {
  padding: 12px 16px;
  border-radius: 8px; /* Hafif yuvarlak köşeler */
  border: 1px solid #ccc;
  font-size: 16px;
  outline: none;
  transition: border-color 0.2s;
  background-color: #fff;
}

.s-input:focus {
  border-color: #1428a0; /* Odaklanınca mavi olur */
}
</style>