<script setup>
import TechIcon from '../atoms/TechIcon.vue';

defineProps({
  image: String,
  title: String,
  price: String
});
</script>

<template>
  <div class="product-card">
    
    <div class="image-container">
      <img :src="image" :alt="title" class="prod-img" />
    </div>

    <div class="info-container">
      <h3 class="prod-title">{{ title }}</h3>
      
      <div class="icon-row">
        <TechIcon />
        <TechIcon />
      </div>

      <div class="prod-price">{{ price }} TL</div>
    </div>

  </div>
</template>

<style scoped>
.product-card {
  min-width: 280px; 
  max-width: 280px;
  display: flex;
  flex-direction: column;
  gap: 20px;
  cursor: pointer;
}

.image-container {
  width: 100%;
  aspect-ratio: 1 / 1; 
  background-color: #f7f7f7; 
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  transition: background-color 0.3s;
}


.prod-img {
  width: 70%;
  height: auto;
  object-fit: contain;
  transition: transform 0.3s;
}

.product-card:hover .prod-img {
  transform: scale(1.05);
}

.info-container {
  text-align: left;
  padding: 0 5px;
}

.prod-title {
  font-size: 16px;
  font-weight: 700;
  color: #000;
  margin: 0 0 15px 0;
  min-height: 40px; 
}

.icon-row {
  display: flex;
  margin-bottom: 20px;
}

.prod-price {
  font-size: 16px;
  font-weight: 700;
  color: #000;
}
</style>