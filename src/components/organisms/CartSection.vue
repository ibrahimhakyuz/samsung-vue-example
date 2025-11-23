<script setup>
import { ref, computed } from 'vue';
import BaseButton from '../atoms/BaseButton.vue';
import CartItem from '../molecules/CartItem.vue';

const couponCode = ref('');
const quantity = ref(1);

const product = {
  id: 101,
  title: 'Galaxy Z Flip7',
  variantInfo: 'Mercan, 512 GB',
  sku: 'SM-F766BZRHTUR',
  stockStatus: 'Stokta var',
  price: '77.499,00 TL',
  image: 'https://static.ticimax.cloud/cdn-cgi/image/width=-,quality=85/58097/uploads/urunresimleri/buyuk/nothing-phone-2-d8c73e.png'
};

const parsePrice = (priceStr) => {
  return parseFloat(
    priceStr.replace(' TL', '').replaceAll('.', '').replace(',', '.')
  );
};

const formatPrice = (amount) => {
  return amount.toLocaleString('tr-TR', {
    minimumFractionDigits: 2,
    maximumFractionDigits: 2
  }) + ' TL';
};

const totalPrice = computed(() => {
  const unitPrice = parsePrice(product.price);
  const total = unitPrice * quantity.value;
  return formatPrice(total);
});
</script>

<template>
  <div class="cart-wrapper">
    
    <div class="cart-left">

      <CartItem 
        v-model="quantity"
        :image="product.image"
        :title="product.title"
        :variantInfo="product.variantInfo"
        :sku="product.sku"
        :stockStatus="product.stockStatus"
        :price="product.price"
      />
      
    </div>

    <div class="cart-right">
      <div class="summary-card">
        
        <div class="coupon-section">
          <label>Kupon kullanın</label>
          <div class="coupon-input-group">
            <input type="text" v-model="couponCode" placeholder="Kupon kodunu girin" />
            
            <BaseButton variant="primary" class="coupon-btn">
              Uygula
            </BaseButton>
          </div>
        </div>

        <h3 class="summary-title">Özet</h3>
        
        <div class="summary-row">
          <span>Ara toplam</span>
          <span>{{ totalPrice }}</span>
        </div>

        <div class="summary-total">
          <span>Toplam</span>
          <span>{{ totalPrice }}</span>
        </div>

        <p class="rewards-info">
          Bu siparişinizden Samsung Rewards puanı kazanmak için giriş yapın
        </p>
        <p class="rewards-info bold">
          Bu siparişten Samsung Rewards puanı kazanın <small>(sadece Samsung Rewards üyelerine özel) ⓘ</small>
        </p>

        <BaseButton block variant="blue" style="font-size:16px;">
          Sepeti onayla
        </BaseButton>

        <ul class="trust-list">
          <li>
            <svg class="trust-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="3" width="15" height="13"></rect><polygon points="16 8 20 8 23 11 23 16 16 16 16 8"></polygon><circle cx="5.5" cy="18.5" r="2.5"></circle><circle cx="18.5" cy="18.5" r="2.5"></circle></svg>
            <span>Ücretsiz teslimat</span>
          </li>
          <li>
            <svg class="trust-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path></svg>
            <span>Samsung güvencesi</span>
          </li>
          <li>
            <svg class="trust-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="2" y="4" width="20" height="16" rx="2"></rect><line x1="2" y1="10" x2="22" y2="10"></line></svg>
            <span>Samsung Rewards ile her siparişte puan kazanma fırsatı</span>
          </li>
          <li>
            <svg class="trust-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path><polyline points="22 4 12 14.01 9 11.01"></polyline></svg>
            <span>Samsung Electronics Türkiye garantisi</span>
          </li>
        </ul>

      </div>
    </div>
  </div>
</template>

<style scoped>
.cart-wrapper {
  display: flex;
  gap: 40px;
  padding: 40px;
  max-width: 1400px;
  margin: 0 auto;
  color: #000;
  align-items: flex-start;
}

.cart-left {
  flex: 2;
  padding-top: 30px;
}

.cart-right {
  flex: 1;
  min-width: 380px;
}

.summary-card {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 30px;
  background: #fff;
}

.coupon-section { 
  margin-bottom: 30px; 
  border-bottom: 1px solid #a4a4a4; 
  padding-bottom: 15px; 
}
.coupon-section label { 
  font-size: 12px; 
  color: #666; 
  display: block; 
  margin-bottom: 8px; 
}
.coupon-input-group {
  display: flex;
  align-items: center;
  gap: 10px; 
}
.coupon-input-group input {
  flex: 1; 
  border: none; 
  outline: none; 
  font-size: 14px; 
  padding: 8px 0;
  border-bottom: 1px solid transparent;
  transition: border-color 0.2s;
}
.coupon-input-group input:focus {
  border-bottom: 1px solid #000;
}

.coupon-btn {
  padding: 6px 20px !important; 
  font-size: 12px !important;
  border-radius: 20px !important;
}

.summary-title { font-size: 22px; font-weight: 700; margin-bottom: 20px; }

.summary-row {
  display: flex; justify-content: space-between; font-size: 14px; margin-bottom: 20px; padding-bottom: 10px; color: #333; border-bottom: 1px solid #a4a4a4;
}

.summary-total {
  display: flex; justify-content: space-between; font-size: 22px; font-weight: 700; margin-bottom: 20px;
}

.rewards-info { font-size: 12px; line-height: 1.4; margin-bottom: 15px; color: #333; }
.rewards-info.bold { font-weight: 600; margin-bottom: 20px; }

.trust-list {
  list-style: none; padding: 0; margin-top: 25px;
}
.trust-list li {
  display: flex; align-items: flex-start; gap: 10px; margin-bottom: 12px; font-size: 11px; font-weight: 600; color: #000;
}
.trust-icon { width: 18px; height: 18px; flex-shrink: 0; }

@media (max-width: 900px) {
  .cart-wrapper { flex-direction: column; }
  .cart-right { width: 100%; min-width: auto; }
}
</style>