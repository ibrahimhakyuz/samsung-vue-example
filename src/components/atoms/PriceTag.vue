<script setup>
defineProps({
  price: {
    type: [String, Number],
    required: true
  },
  currency: {
    type: String,
    default: 'TL'
  },
  size: {
    type: String,
    default: 'medium' // 'small', 'medium', 'large'
  },
  oldPrice: String 
});
</script>

<template>
  <div :class="['price-container', size]">
    <span v-if="oldPrice" class="old-price">
      {{ oldPrice }} {{ currency }}
    </span>  
    <span class="current-price">{{ price }} <small>{{ currency }}</small></span>
  </div>
</template>

<style scoped>
.price-container {
  display: flex;
  flex-direction: column;
  font-family: sans-serif;
}

.current-price {
  font-weight: 700;
  color: #000;
}

.current-price small {
  font-size: 0.7em;
}

.old-price {
  text-decoration: line-through;
  color: #777;
  font-size: 0.9em;
  margin-bottom: 2px;
}

.small .current-price { font-size: 14px; }
.medium .current-price { font-size: 18px; }
.large .current-price { font-size: 24px; }
</style>