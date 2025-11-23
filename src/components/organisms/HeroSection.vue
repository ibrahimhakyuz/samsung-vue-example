<script setup>
import BaseButton from '../atoms/BaseButton.vue';
import localVideoUrl from '@/assets/hero-video.mp4'; 
</script>

<template>
  <section class="hero-section">
    <video autoplay muted loop playsinline class="bg-video">
      <source :src="localVideoUrl" type="video/mp4">
    </video>

    <div class="hero-content">
      <h1 class="hero-title">Kasım<br>Fırsatları</h1>
      <p class="hero-subtitle">AI ile güçlenen ürünlerimizi<br>keşfedin</p>
      
      <div class="btn-wrapper">
        <BaseButton variant="outline" class="custom-hero-btn">Daha fazla bilgi</BaseButton>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  position: relative;
  width: 100%;
  height: 100vh; 
  overflow: hidden;
  display: flex;
  align-items: center; 
}

.bg-video {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  object-fit: cover;
  z-index: 0;
}

.hero-content {
  position: relative;
  z-index: 1; 
  max-width: 1600px;
  width: 100%;
  margin: 0 auto;
  padding-left: 120px; 
  color: white;
  margin-top: 60px; 
}

.hero-title {
  font-size: 64px;
  font-weight: 700;
  line-height: 1.1;
  margin-bottom: 20px;
}

.hero-subtitle {
  font-size: 24px;
  font-weight: 400;
  margin-bottom: 40px;
}

:deep(.custom-hero-btn) {
  border-color: white !important;
  color: white !important;
  border-radius: 30px;
  padding: 12px 36px;
  font-size: 14px;
}
:deep(.custom-hero-btn:hover) {
  background: white !important;
  color: black !important;
}
</style>