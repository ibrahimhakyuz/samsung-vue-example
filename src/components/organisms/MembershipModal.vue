<script setup>
import BaseButton from '../atoms/BaseButton.vue';

const menuItems = [
  'Samsung Members', 'Siparişlerim', 'Ürünlerim', 'Samsung Rewards'
];
</script>

<template>
  <div class="dropdown-card">
    <h3 class="dropdown-header">Giriş yap/Üye ol</h3>
    
    <div class="promo-text">
      <span>Receive up to 4% of your purchase back in points.</span>
      <span class="arrow">›</span>
    </div>

    <ul class="dropdown-menu">
      <li v-for="item in menuItems" :key="item">
        <a href="#">{{ item }}</a>
      </li>
    </ul>

    <div class="auth-actions">
      <BaseButton block variant="primary" style="font-size: 12px; padding: 8px;">Giriş Yap</BaseButton>
      <a href="#" class="signup-link">Üye Ol</a>
    </div>
  </div>
</template>

<style scoped>
.dropdown-card {
  position: absolute;
  top: 100%;
  right: 0;
  width: 280px;
  background: white;
  border-radius: 20px;
  box-shadow: 0 10px 40px rgba(0,0,0,0.15);
  padding: 24px;
  border: 1px solid #eee;
  z-index: 1100;
  margin-top: 10px;
  text-align: left;
  color: #000;
  cursor: default;
}

.dropdown-header {
  font-size: 18px;
  font-weight: 700;
  margin: 0 0 15px 0;
  color: #000;
}

.promo-text {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 12px;
  color: #555;
  padding-bottom: 15px;
  margin-bottom: 15px;
  border-bottom: 1px solid #eee;
  cursor: pointer;
}
.promo-text:hover { color: #1428a0; }
.arrow { font-size: 16px; font-weight: bold; }

.dropdown-menu {
  list-style: none;
  padding: 0;
  margin: 0 0 20px 0;
}

.dropdown-menu li {
  margin-bottom: 12px;
}

.dropdown-menu a {
  text-decoration: none;
  color: #000;
  font-size: 14px;
  font-weight: 500;
  display: block;
  transition: color 0.2s;
}

.dropdown-menu a:hover {
  color: #1428a0;
}

.auth-actions {
  display: flex;
  flex-direction: column;
  gap: 10px;
  text-align: center;
}

.signup-link {
  font-size: 12px;
  color: #000;
  text-decoration: underline;
}
.signup-link:hover { color: #555; }
</style>