<script setup>

const menuItems = [
  'Samsung Members',
  'Siparişlerim',
  'Ürünlerim',
  'Samsung Rewards'
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

  </div>
</template>

<style scoped>
.dropdown-card {
  position: absolute;
  top: 100%;
  right: 0;
  width: 215px; 
  background: white;
  border-radius: 26px;        
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.18);
  padding: 22px 24px;
  border: 1px solid #e5e5e5;
  z-index: 1100;
  margin-top: 10px;
  text-align: left;
  color: #000;
  cursor: default;
}

.dropdown-header {
  font-size: 15px;
  font-weight: 700;
  margin: 0 0 16px 0;
}

.promo-text {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 11px;
  line-height: 1.4;
  color: #252525;
  padding-bottom: 14px;
  margin-bottom: 16px;
  border-bottom: 1px solid #e4e4e4;
}
.arrow {
  font-size: 17px;
  font-weight: 600;
  opacity: 0.7;
}

.dropdown-menu {
  list-style: none;
  padding: 0;
  margin: 0;
}

.dropdown-menu li {
  margin-bottom: 14px;
}

.dropdown-menu a {
  text-decoration: none;
  color: #252525;
  font-size: 13px;
  letter-spacing: 0.1px;
  transition: color 0.2s ease;
}

</style>
