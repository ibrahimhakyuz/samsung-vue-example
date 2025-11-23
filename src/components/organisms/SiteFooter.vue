<script setup>
import FooterColumn from '../molecules/FooterColumn.vue';

const columns = [
  {
    title: 'Alışveriş',
    links: [
      'Mağaza Ana Sayfası', 'Samsung\'dan Kazançlı Alın', 'SmartThings', 
      'AI Ürünlerini Keşfedin', 'Samsung Deneyim Mağazası', 'Samsung Çalışanlarına Özel',
      'İş Ortaklarına Özel', 'Kamu Çalışanlarına Özel', 'Eğitim İndirimi', 'SSS',
      'Samsung Rewards', 'Samsung Affiliate Programı', 'Keşfedin'
    ]
  },
  {
    title: 'Ürünler',
    links: [
      'Galaxy Akıllı Telefon', 'Galaxy Tab', 'Galaxy Watch', 'Galaxy Buds', 
      'TV\'ler', 'Projektörler', 'Ses Sistemleri', 'Buzdolapları', 
      'Bulaşık Makineleri', 'Giysi Temizliği', 'Elektrikli Süpürgeler', 
      'Monitörler', 'Hafıza ve Depolama', 'Aksesuarlar'
    ]
  },
  {
    title: 'Destek',
    links: [
      'Destek Anasayfa', 'Kurulum Talebi ↗', 'Kılavuz ve Yazılım', 
      'Samsung Destekte Ara', 'Mağaza Hakkında SSS', 'Garanti Bilgileri',
      'Servis Merkezi', 'Tamir Rezervasyonu Yap', 'Onarım Takip',
      'Kolay Onarım', 'Onarım Maliyeti', 'Canlı Destek ↗', 'Çevrimiçi Destek'
    ]
  },
  {
    title: 'Hesabım',
    links: [
      'Samsung Rewards', 'Siparişlerim ↗', 'Hesabım', 'Ürünlerim', 'Kuponlarım ↗'
    ]
  },
  {
    title: 'Sürdürülebilirlik',
    links: [
      'Çevre', 'Güvenlik ve Gizlilik', 'Erişilebilirlik', 
      'Çeşitlilik · Eşitlik · Kapsayıcılık', 'Kurumsal Vatandaşlık ↗', 
      'Kurumsal Sürdürülebilirlik ↗', 'Solve for Tomorrow', 'Innovation Campus'
    ]
  },
  {
    title: 'Hakkımızda',
    links: [
      'Şirket Bilgileri', 'Faaliyet Alanı', 'Marka Kimliği', 'Kariyer',
      'Yatırımcı İlişkileri', 'Haberler', 'Etik Kurallar', 'Samsung Tasarım'
    ]
  }
];
</script>

<template>
  <footer class="site-footer">
    <div class="footer-grid">
      <FooterColumn 
        v-for="(col, index) in columns" 
        :key="index"
        :title="col.title" 
        :links="col.links"
        class="footer-col-item" 
      />
    </div>

    <div class="footer-bottom-wrapper">
      
      <div class="bottom-row top-section">
        <div class="copyright">
          Telif Hakkı © 1995-2025 Samsung. Tüm Hakları Saklıdır.
        </div>
      </div>

      <div class="bottom-row bottom-section">
        <div class="bottom-links">
          <a href="#">Türkiye/Türkçe</a>
          <span class="separator">|</span>
          <a href="#">Gizlilik Politikası</a>
          <a href="#">Kişisel Veriler</a>
          <a href="#">Kullanım Şartları</a>
        </div>

        <div class="social-media">
          <span class="follow-text">Bizi Takip Edin</span>
          <div class="icons">
            <a href="#"><svg viewBox="0 0 24 24" width="24" height="24" fill="currentColor"><path d="M12 2.04c-5.5 0-10 4.49-10 10.02c0 5 3.66 9.15 8.44 9.9v-7H7.9v-2.9h2.54V9.85c0-2.51 1.49-3.89 3.78-3.89c1.09 0 2.23.19 2.23.19v2.47h-1.26c-1.24 0-1.63.77-1.63 1.56v1.88h2.78l-.45 2.9h-2.33v7a10 10 0 0 0 8.44-9.9c0-5.53-4.5-10.02-10-10.02Z"></path></svg></a>
            
            <a href="#"><svg viewBox="0 0 24 24" width="24" height="24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"></path></svg></a>

            <a href="#"><svg viewBox="0 0 24 24" width="24" height="24" fill="currentColor"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zM12 16a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm6.406-11.845a1.44 1.44 0 1 0 0 2.881 1.44 1.44 0 0 0 0-2.881z"></path></svg></a>

            <a href="#"><svg viewBox="0 0 24 24" width="24" height="24" fill="currentColor"><path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"></path></svg></a>
          </div>
        </div>
      </div>

    </div>
  </footer>
</template>

<style scoped>
.site-footer {
  background-color: #fff;
  padding: 60px 40px 20px;
  border-top: 1px solid #e0e0e0;
  font-family: 'Inter', sans-serif;
}

.footer-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  max-width: 1440px;
  margin: 0 auto 0px auto; 
  align-items: stretch;
}

.footer-col-item {
  border-right: 1px solid #e0e0e0;
  padding-right: 20px;
}
.footer-col-item:last-child {
  border-right: none;
}


.footer-bottom-wrapper {
  max-width: 1440px;
  margin: 0 auto;
  font-size: 12px;
  color: #666;
}

.bottom-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
}

.top-section {
  padding-bottom: 30px;
  border-bottom:1px solid #e0e0e0 ;
}


.divider {
  height: 1px;
  background-color: #e0e0e0;
  width: 100%;
}

.bottom-section {
  padding-top: 15px;
  flex-wrap: wrap;
  gap: 15px;
}

.bottom-links {
  display: flex;
  align-items: center;
  gap: 15px;
  flex-wrap: wrap;
}

.bottom-links a {
  color: #333;
  text-decoration: none;
}


.separator {
  color: #ccc;
  font-weight: 300;
}

.social-media {
  display: flex;
  align-items: center;
  gap: 15px;
}

.follow-text {
  font-weight: 600;
  color: #000;
}

.icons {
  display: flex;
  gap: 12px;
}

.icons a {
  color: #000;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: color 0.2s;
}



</style>