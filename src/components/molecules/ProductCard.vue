<script setup>
import BaseButton from '../atoms/BaseButton.vue';
import PriceTag from '../atoms/PriceTag.vue';

defineProps({
  image: String,
  title: String,
  price: String,
  isNew: Boolean
});
</script>

<template>
  <div class="product-card-molecule">
    <div class="card-badge" v-if="isNew">Yeni</div>
    
    <div class="image-area">
      <div class="img-placeholder">
        <span>{{ title }} Görseli</span>
      </div>
    </div>

    <h3 class="product-title">{{ title }}</h3>

    <div class="price-area">
      <PriceTag :price="price" size="medium" />
    </div>

    <div class="action-area">
      <BaseButton variant="primary" class="buy-btn">Satın Al</BaseButton>
    </div>
  </div>
</template>

<style scoped>
.product-card-molecule {
  width: 260px;
  padding: 20px;
  background: white;
  border-radius: 20px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  transition: box-shadow 0.3s;
  border: 1px solid #f0f0f0;
}

.product-card-molecule:hover {
  box-shadow: 0 10px 30px rgba(0,0,0,0.1);
}

.card-badge {
  position: absolute;
  top: 15px;
  left: 15px;
  background-color: #000;
  color: #fff;
  font-size: 10px;
  padding: 4px 8px;
  border-radius: 10px;
  font-weight: bold;
}

.image-area {
  width: 100%;
  height: 180px;
  margin-bottom: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.img-placeholder {
  width: 100%;
  height: 100%;
  background-color: #f4f4f4;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #999;
  font-size: 12px;
}

.product-title {
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 10px;
  min-height: 50px; 
  display: flex;
  align-items: center;
  justify-content: center;
}

.price-area {
  margin-bottom: 20px;
}

.action-area {
  width: 100%;
}

:deep(.buy-btn) {
  width: 100%;
}
</style>