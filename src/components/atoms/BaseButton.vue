<script setup>
defineProps({
  variant: {
    type: String,
    default: 'primary', 
    validator: (val) => ['primary', 'blue', 'outline', 'ghost', 'dark-gray'].includes(val)
  },
  block: {
    type: Boolean,
    default: false
  }
});
</script>

<template>
  <button :class="['s-btn', variant, { 'full-width': block }]">
    <slot />
  </button>
</template>

<style scoped>
.s-btn {
  padding: 10px 24px;
  border-radius: 25px; 
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  border: 1px solid transparent;
  transition: all 0.2s ease;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px; 
}

.primary {
  background-color: #000;
  color: #fff;
}
.primary:hover {
  background-color: #333;
}

.blue {
  background-color: #1428a0;
  color: #fff;
  border: none; 
}
.blue:hover {
  background-color: #0f1c6e;
}


.outline {
  background-color: transparent;
  border: 1px solid #ccc;
  color: #000;
}
.outline:hover {
  background-color: #f8f8f8;
  border-color: #000;
}


.dark-gray {
  background-color: #666;
  color: #fff;
  border: none;
}
.dark-gray:hover {
  background-color: #555;
}

.ghost {
  background-color: transparent;
  color: #000;
  text-decoration: underline;
  padding: 0;
}
.ghost:hover {
  color: #555;
}

.full-width {
  width: 100%;
}
</style>