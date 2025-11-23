<script setup>

import SiteHeader from './components/organisms/SiteHeader.vue';
import HeroSection from './components/organisms/HeroSection.vue';
import SiteFooter from './components/organisms/SiteFooter.vue';
import LoginForm from './components/organisms/LoginForm.vue';
import SignupForm from './components/organisms/SignupForm.vue';
import ProductDetail from './components/organisms/ProductDetail.vue';
import CartSection from './components/organisms/CartSection.vue';
import ProductSlider from './components/organisms/ProductSlider.vue';


</script>

<template>
  <div class="app-container">
    
      <SiteHeader/>
      <HeroSection />
      <ProductDetail/>
      <CartSection/>
      <ProductSlider/>
      <LoginForm/>
      <SignupForm/>
      <SiteFooter/>


  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

body {
  margin: 0;
  padding: 0;
  font-family: 'Inter', sans-serif;
  background-color: white;
}
</style>

<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  overflow: hidden;
}


</style>