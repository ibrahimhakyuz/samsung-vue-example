<script setup>
import { ref } from 'vue';
import SliderProductCard from '../molecules/SliderProductCard.vue';

const products = [
  { 
    id: 1, 
    title: 'Galaxy Z Flip7', 
    price: '69.499,00', 
    image: 'https://static.ticimax.cloud/cdn-cgi/image/width=-,quality=85/58097/uploads/urunresimleri/buyuk/nothing-phone-2-d8c73e.png' 
  },
  { 
    id: 2, 
    title: 'Galaxy Z Flip7 FE', 
    price: '65.499,00', 
    image: 'https://static.ticimax.cloud/cdn-cgi/image/width=-,quality=85/58097/uploads/urunresimleri/buyuk/nothing-phone-2-d8c73e.png' 
  },
  { 
    id: 3, 
    title: 'Galaxy Z Fold7', 
    price: '127.499,00', 
    image: 'https://static.ticimax.cloud/cdn-cgi/image/width=-,quality=85/58097/uploads/urunresimleri/buyuk/nothing-phone-2-d8c73e.png' 
  },
  { 
    id: 4, 
    title: "Galaxy Z Flip7 (Samsung.com'a özel)", 
    price: '77.499,00', 
    image: 'https://static.ticimax.cloud/cdn-cgi/image/width=-,quality=85/58097/uploads/urunresimleri/buyuk/nothing-phone-2-d8c73e.png' 
  },
  { 
    id: 5, 
    title: 'Galaxy Buds3', 
    price: '4.749,00', 
    image: 'https://static.ticimax.cloud/cdn-cgi/image/width=-,quality=85/58097/uploads/urunresimleri/buyuk/nothing-phone-2-d8c73e.png' 
  },
  { 
    id: 6, 
    title: 'Galaxy Watch 7', 
    price: '7.999,00', 
    image: 'https://static.ticimax.cloud/cdn-cgi/image/width=-,quality=85/58097/uploads/urunresimleri/buyuk/nothing-phone-2-d8c73e.png' 
  },
];

const sliderRef = ref(null);
const scrollProgress = ref(0); 

const scrollLeft = () => {
  if (sliderRef.value) {
    sliderRef.value.scrollBy({ left: -320, behavior: 'smooth' });
  }
};

const scrollRight = () => {
  if (sliderRef.value) {
    sliderRef.value.scrollBy({ left: 320, behavior: 'smooth' });
  }
};

const onScroll = () => {
  const el = sliderRef.value;
  if (el) {
    const maxScroll = el.scrollWidth - el.clientWidth;
    const currentScroll = el.scrollLeft;
    scrollProgress.value = (currentScroll / maxScroll) * 100;
  }
};
</script>

<template>
  <section class="rec-section">
    <div class="content-wrapper">
      <h2 class="section-title">Sizin için önerilenler</h2>
      
      <div class="slider-container" ref="sliderRef" @scroll="onScroll">
        <SliderProductCard 
          v-for="product in products" 
          :key="product.id"
          :title="product.title"
          :price="product.price"
          :image="product.image"
        />
      </div>

      <div class="controls-area">
        
        <div class="progress-track">
          <div class="progress-bar" :style="{ width: scrollProgress + '%' }"></div>
        </div>

        <div class="nav-buttons">
          <button class="arrow-btn" @click="scrollLeft">
             <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M15 18l-6-6 6-6"></path></svg>
          </button>
          <button class="arrow-btn" @click="scrollRight">
             <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M9 18l6-6-6-6"></path></svg>
          </button>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
.rec-section {
  padding: 60px 0;
  background: #fff;
}

.content-wrapper {
  max-width: 1440px;
  margin: 0 auto;
  padding: 0 80px;
}

.section-title {
  font-size: 34px;
  font-weight: 700;
  margin-bottom: 40px;
  text-align: left;
  color: #000;
}

.slider-container {
  display: flex;
  gap: 24px;
  overflow-x: auto;
  padding-bottom: 20px;
  scroll-behavior: smooth;
  scrollbar-width: none; 
}
.slider-container::-webkit-scrollbar {
  display: none;
}

.controls-area {
  display: flex;
  align-items: center;   
  justify-content: center;
  gap: 20px;                 
  margin-top: 20px;
  width: 100%;              
}

.progress-track {
  flex: 1; 
  height: 2px;
  background-color: #ddd;
  margin-right: 40px;
  position: relative;
  max-width: 60%; 
}

.progress-bar {
  height: 100%;
  background-color: #000; 
  width: 0%;
  position: absolute;
  top: 0;
  left: 0;
  transition: width 0.1s;
}

.nav-buttons {
  display: flex;
  gap: 10px;
}

.arrow-btn {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  border: 1px solid #777777;
  background: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  color: #000;
  transition: all 0.2s;
}

.arrow-btn:hover {
  border-color: #a9a9a9;
  color: #878787;
}


</style>