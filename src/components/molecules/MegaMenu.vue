<script setup>
import { computed } from 'vue';

const props = defineProps({
  isOpen: Boolean,
  activeCategory: String
});

const menuData = {
  magaza: {
    products: [
      { name: 'Galaxy Z Fold7', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Z Flip7', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy S25 Ultra', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Tab S11', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Watch8', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Buds3 Pro', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Buds3 Pro', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Buds3 Pro', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Buds3 Pro', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
    ],
    links: ['Samsung\'dan Kazançlı Alın', 'Kampanyalar', 'Samsung Shop App\'i İndirin', 'SmartThings', 'Al Ürünlerini Keşfedin']
  },
  mobil: {
    products: [
      { name: 'Galaxy S Serisi', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Z Serisi', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy A Serisi', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Tabletler', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'One UI', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' }
    ],
    links: ['Telefonları Keşfedin', 'Galaxy Al', 'One UI', 'Samsung Health', 'Uygulamalar & Hizmetler']
  },
  tv: {
    products: [
      { name: 'Neo QLED 8K', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'OLED 4K', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'The Frame', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Soundbar', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Projektör', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' }
    ],
    links: ['Samsung Vision Al', 'Neden Samsung TV', 'Neden OLED', 'Neden Neo QLED']
  },
  beyaz: {
    products: [
      { name: 'Bespoke AI', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Buzdolapları', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Çamaşır Makineleri', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Klimalar', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Süpürgeler', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' }
    ],
    links: ['Bespoke Al', 'Smart Forward', 'Al Enerji Tasarrufu', 'Neden Samsung Ev Aletleri']
  },
  monitor: {
    products: [
      { name: 'Odyssey OLED', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'ViewFinity', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Smart Monitor', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'SSD & Hafıza', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' }
    ],
    links: ['Neden Odyssey Gaming Monitör', 'Neden ViewFinity Monitör', 'Neden Smart Monitör', 'Monitör Seçmeme Yardım Et']
  },
  giyilebilir: {
    products: [
      { name: 'Galaxy Watch Ultra', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Watch7', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Buds3', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Galaxy Ring', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' }
    ],
    links: ['Samsung Health', 'Galaxy Al', 'Uygulamalar & Hizmetler', 'Neden Galaxy']
  },
  aksesuar: {
    products: [
      { name: 'Telefon Kılıfları', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Şarj Aletleri', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'Saat Kayışları', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' },
      { name: 'SmartTag2', img: 'https://crdms.images.consumerreports.org/prod/products/cr/models/399694-smartphones-apple-iphone-11-10008711.png' }
    ],
    
  }
};

const currentContent = computed(() => {
  return menuData[props.activeCategory] || { products: [], links: [] };
});
</script>

<template>
  <div v-if="isOpen" class="mega-menu-wrapper">
    <div class="menu-inner">
       
      <div class="products-grid">
        <div v-for="(prod, index) in currentContent.products" :key="index" class="menu-product-item">
          <div class="img-box">
            <img :src="prod.img" :alt="prod.name">
          </div>
          <span class="prod-name">{{ prod.name }}</span>
        </div>
      </div>

      <div class="discover-list">
        <h4 class="list-title">KEŞFEDİN</h4>
        <ul>
          <li v-for="link in currentContent.links" :key="link">
            <a href="#">{{ link }}</a>
          </li>
        </ul>
      </div>

    </div>
  </div>
</template>

<style scoped>
.mega-menu-wrapper {
  position: absolute;
  left: 0;
  width: 100%;
  background: white;
  border-bottom: 1px solid #e0e0e0;
  padding: 40px 0;
  z-index: 900;
  box-shadow: 0 10px 30px rgba(0,0,0,0.05);
}

.menu-inner {
  display: flex;
  max-width: 1600px;
  margin: 0 auto;
  padding: 0 40px;
}

.products-grid {
  flex: 3; 
  display: flex;
  flex-wrap: wrap;
  gap: 40px 20px; 
  border-right: 1px solid #f0f0f0;
  padding-right: 40px;
}

.menu-product-item {
  color: #010101;
  width: 180px;
  text-align: center;
  cursor: pointer;
}

.menu-product-item:hover .prod-name {
  text-decoration: none;
}

.img-box {
  width: 100%;
  height: 90px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 12px;
}

.img-box img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
  transition: all 0.5s ease;
}
.img-box img:hover{
  scale: 110%;
}

.prod-name {
  font-size: 13px;
  font-weight: 600;
  color: #000;
  line-height: 1.4;
}

.discover-list {
  flex: 1; 
  padding-left: 40px;
}

.list-title {
  font-size: 15px;
  color: #757575;
  font-weight: 600;
  margin-bottom: 20px;
  letter-spacing: 0.5px;
}

.discover-list ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.discover-list li {
  margin-bottom: 12px;
}

.discover-list a {
  text-decoration: none;
  color: #1e1e1e;
  font-size: 14px;
  font-weight: 500;
}

.discover-list a:hover {
  color: #757575;
}
</style>