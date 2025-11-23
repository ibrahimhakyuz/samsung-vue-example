<script setup>
const props = defineProps({
  image: String,
  title: String,
  variantInfo: String,
  sku: String,
  stockStatus: String,
  price: String,
  modelValue: Number
});

const emit = defineEmits(['update:modelValue']);

const increase = () => emit('update:modelValue', props.modelValue + 1);
const decrease = () => {
  if (props.modelValue > 1) emit('update:modelValue', props.modelValue - 1);
};
</script>

<template>
  <div class="cart-item-molecule">
    
    <div class="prod-img-wrapper">
      <img :src="image" :alt="title" />
    </div>
    
    <div class="prod-details">
      <h3 class="prod-title">{{ title }}</h3>
      <p class="prod-variant">{{ variantInfo }}</p>
      <p class="prod-sku">{{ sku }}</p>
      <p class="prod-stock">{{ stockStatus }}</p>
    </div>

    <div class="prod-actions">
      
      <div class="top-action-group">
        <span class="price">{{ price }}</span>
        <button class="delete-btn">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
            <polyline points="3 6 5 6 21 6"></polyline>
            <path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"></path>
          </svg>
        </button>
      </div>
      
      <div class="quantity-selector">
        <button @click="decrease" :disabled="modelValue <= 1" class="qty-btn">−</button>
        <span class="qty-value">{{ modelValue }}</span>
        <button @click="increase" class="qty-btn">+</button>
      </div>

    </div>

  </div>
</template>

<style scoped>
.cart-item-molecule {
  display: flex;
  padding-bottom: 30px; 
  background: #fff;
}

.prod-img-wrapper {
  width: 200px;
  height: 200px;
  flex-shrink: 0;
}
.prod-img-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.prod-details {
  flex: 1;
  padding: 10px 20px 0 20px;
  display: flex;
  flex-direction: column;
}

.prod-title {
  font-size: 22px;
  font-weight: 700;
  margin: 0 0 12px 0;
  color: #000;
}

.prod-variant, .prod-sku {
  font-size: 10px;
  color: #333;
  margin: 0 0 6px 0;
}

.prod-stock {
  font-size: 10px;
  color: #333;
}

.prod-actions {
  display: flex;
  flex-direction: column;
  justify-content: space-between; 
  align-items: flex-end;
  min-width: 160px;
  padding-top: 10px;
}

.top-action-group {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 10px; 
}

.price {
  font-size: 20px;
  font-weight: 700;
  color: #000;
}

.delete-btn {
  background: none;
  border: none;
  cursor: pointer;
  color: #000;
  padding: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.delete-btn:hover {
  opacity: 0.7;
}

.quantity-selector {
  display: flex;
  align-items: center;
  border: 1px solid #ddd;
  border-radius: 50px; 
  background-color: #fff;
  overflow: hidden;
  height: 40px; 
}

.qty-btn {
  width: 40px;
  height: 100%;
  border: none;
  background: #fff;
  font-size: 18px;
  color: #000;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.2s;
}

.qty-btn:hover:not(:disabled) {
  background-color: #f5f5f5;
}

.qty-btn:disabled {
  color: #ccc;
  cursor: default;
}

.qty-value {
  width: 40px;
  text-align: center;
  font-size: 16px;
  font-weight: 400;
  color: #000;
  border-left: 1px solid #eee;
  border-right: 1px solid #eee;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>