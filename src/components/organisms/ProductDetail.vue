<script setup>
import { ref, computed } from 'vue';

const selectedStorage = ref('512 GB');
const selectedColorName = ref('Mint Yeşili');
const currentSlideIndex = ref(0);


const galleryImages = [
  'https://images.samsung.com/tr/smartphones/galaxy-z-flip6/images/galaxy-z-flip6-share-image.jpg',
  'https://images.pexels.com/photos/1092644/pexels-photo-1092644.jpeg?cs=srgb&dl=pexels-fotios-photos-1092644.jpg&fm=jpg',
  'https://images.samsung.com/is/image/samsung/p6pim/tr/sm-f741blgatur/gallery/tr-galaxy-z-flip6-f741-sm-f741blgatur-541858160?$684_547_PNG$'
];

const colors = [
  { name: 'Mint Yeşili', code: '#d4e7d8', exclusive: true },
  { name: 'Gölge Mavisi', code: '#3d4f75', exclusive: false },
  { name: 'Gece Siyahı', code: '#333333', exclusive: false },
  { name: 'Mercan', code: '#ff7f50', exclusive: false }
];

const storageOptions = [
  { size: '256 GB', ram: '12 GB', price: '69.499,00 TL' },
  { size: '512 GB', ram: '12 GB', price: '77.499,00 TL' }
];

const features = [
  { icon: '⛶', title: 'En Geniş FlexWindow' },
  { icon: '📷', title: '50 MP Selfie Kamerası' },
  { icon: '✨', title: 'Galaxy AI'}
];

const selectedColorObj = computed(() => {
  return colors.find(c => c.name === selectedColorName.value) || colors[0];
});

const nextSlide = () => {
  if (currentSlideIndex.value < galleryImages.length - 1) {
    currentSlideIndex.value++;
  } else {
    currentSlideIndex.value = 0;
  }
};

const prevSlide = () => {
  if (currentSlideIndex.value > 0) {
    currentSlideIndex.value--;
  } else {
    currentSlideIndex.value = galleryImages.length - 1;
  }
};

const setSlide = (index) => {
  currentSlideIndex.value = index;
};
</script>

<template>
  <div class="product-wrapper">
    
    <div class="gallery-section">
      <div class="gallery-container">
        <div class="image-area">
          <transition name="fade" mode="out-in">
            <img 
              :key="currentSlideIndex"
              :src="galleryImages[currentSlideIndex]" 
              alt="Galaxy Z Flip7" 
              class="product-img" 
            />
          </transition>
        </div>
        <button class="nav-btn prev" @click="prevSlide">‹</button>
        <button class="nav-btn next" @click="nextSlide">›</button>
        <div class="pagination-dots">
          <span 
            v-for="(img, index) in galleryImages" 
            :key="index"
            class="dot" 
            :class="{ active: currentSlideIndex === index }"
            @click="setSlide(index)"
          ></span>
        </div>
      </div>
    </div>

    <div class="details-section">
      
      <div class="features-banner">
        <div v-for="(feat, index) in features" :key="index" class="feat-item">
          <div class="feat-icon">{{ feat.icon }}</div>
          <div class="feat-text">
            <span>{{ feat.title }}</span>
          </div>
        </div>
      </div>

      <div class="selection-group">
        <h3 class="group-title">Cihaz</h3>
        <div class="option-card active fixed-device">
          <span class="opt-name">Galaxy Z Flip7</span>
          <span class="opt-price">77.499,00 TL</span>
        </div>
      </div>

      

      <div class="selection-group">
        <h3 class="group-title">Hafıza | Ram</h3>
        <div class="storage-list">
          <div 
            v-for="option in storageOptions" 
            :key="option.size"
            class="option-card"
            :class="{ active: selectedStorage === option.size }"
            @click="selectedStorage = option.size"
          >
            <span class="opt-name">{{ option.size }} | {{ option.ram }}</span>
            <span class="opt-price">{{ option.price }}</span>
          </div>
        </div>
      </div>

      <div class="selection-group">
        <h3 class="group-title">Renk</h3>

        <div class="selected-color-banner">
          <div class="banner-circle" :style="{ backgroundColor: selectedColorObj.code }"></div>
          <div class="banner-info">
            <span class="banner-name">{{ selectedColorObj.name }}</span>
          </div>
        </div>

        <div class="color-grid">
          <div 
            v-for="color in colors" 
            :key="color.name"
            class="color-item-wrapper"
            @click="selectedColorName = color.name"
          >
            <div class="color-circle-outer" :class="{ active: selectedColorName === color.name }">
               <div class="color-circle-inner" :style="{ backgroundColor: color.code }"></div>
            </div>
            <span class="color-label">{{ color.name }}</span>
          </div>
        </div>
      </div>


    </div>
  </div>
</template>

<style scoped>
.product-wrapper {
  display: flex;
  flex-wrap: wrap;
  gap: 60px;
  max-width: 1600px;
  margin: 0 auto;
  padding: 40px;
  font-family: 'Inter', sans-serif;
  align-items: flex-start;
}


.details-section {
  flex: 1;
  min-width: 380px;
  position: relative;
}

.gallery-container {
  background-color: #fff; 
  position: relative;
  width: 850px;      
  height: 500px;     
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;   
}

.product-img {
  width: 850px;
  height: 450px;
  object-fit: cover;  
  transition: transform 0.3s ease;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.nav-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 40px;
  height: 40px;
  background: #fff;
  border: 1px solid #eee;
  border-radius: 50%;
  font-size: 24px;
  cursor: pointer;
  color: #333;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
  transition: all 0.2s;
  z-index: 10;
}
.nav-btn:hover { background: #f9f9f9; }
.prev { left: 7px; }
.next { right: 7px; }

.pagination-dots {
  position: absolute;
  bottom: 0px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 12px;
}

.dot {
  width: 8px;
  height: 8px;
  background: #797979;
  border-radius: 50%;
  cursor: pointer;
}
.dot.active { background: #000; }

.gallery-captions {
  display: flex;
  justify-content: center;
  gap: 40px;
  margin-top: 20px;
  text-align: center;
  font-size: 13px;
  color: #333;
}
.gallery-captions span small {
  color: #007aff;
  font-size: 11px;
}


.features-banner {
  background-color: #f7f7f7;
  border-radius: 16px;
  padding: 20px;
  display: flex;
  justify-content: space-around;
  margin-bottom: 40px;
}

.feat-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  font-size: 11px;
  color: #000;
  font-weight: 600;
}

.feat-icon {
  font-size: 40px;
  margin-bottom: 8px;
  color: #007aff;
}

.selection-group {
  margin-bottom: 80px;
}

.group-title {
  font-size: 24px;
  font-weight: 700;
  margin-bottom: 15px;
  color: #000;
}

.selected-color-banner {
  background-color: #f7f7f7;
  border-radius: 12px;
  padding: 15px 20px;
  display: flex;
  align-items: center;
  gap: 15px;
  margin-bottom: 25px;
}
.banner-circle {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: 1px solid rgba(0,0,0,0.1);
}
.banner-info { display: flex; flex-direction: column; }
.banner-name { font-size: 14px; font-weight: 600; color: #000; }
.banner-exclusive { font-size: 12px; color: #007aff; font-weight: 500; }

.color-grid { display: flex; gap: 20px; justify-content: flex-start; }
.color-item-wrapper { display: flex; flex-direction: column; align-items: center; cursor: pointer; gap: 8px; width: 80px; }
.color-circle-outer {
  width: 44px; height: 44px; border-radius: 50%; display: flex; align-items: center; justify-content: center; border: 1px solid transparent; transition: all 0.2s;
}
.color-circle-outer.active { border: 2px solid #007aff; }
.color-circle-inner {
  width: 34px; height: 34px; border-radius: 50%; border: 1px solid rgba(0,0,0,0.1); box-shadow: 0 0 0 2px #fff;
}
.color-label { font-size: 12px; font-weight: 600; color: #000; text-align: center; line-height: 1.2; }


.storage-list { display: flex; flex-direction: column; gap: 12px; }
.option-card {
  display: flex; justify-content: space-between; align-items: center; padding: 24px; border: 1px solid #d1d1d1; border-radius: 4px; cursor: pointer; background: #fff; transition: all 0.2s ease;
}
.option-card:hover { background-color: #f9f9f9; }
.option-card.active { border: 2px solid #007aff; padding: 23px; }
.fixed-device { cursor: default; background: #fff; }
.opt-name { font-size: 15px; font-weight: 700; color: #000; }
.opt-price { font-size: 15px; color: #333; }

</style>