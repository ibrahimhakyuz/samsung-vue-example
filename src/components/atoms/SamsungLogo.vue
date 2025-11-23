<script setup>
defineProps({
  width: {
    type: String,
    default: '120px'
  }
});
</script>

<template>
  <div class="logo-container" :style="{ width: width }">
    <img 
      src="https://cdn.freebiesupply.com/logos/large/2x/samsung-1-logo-png-transparent.png" 
      alt="Samsung Logo"
      class="s-logo-img"
    />
  </div>
</template>

<style scoped>
.logo-container {
  display: flex;
  align-items: center;
  justify-content: center;
}

.s-logo-img {
  width: 130%;
  height: auto;
  display: block;
}
</style>