<script setup>
import { ref } from 'vue';
import SamsungLogo from '../atoms/SamsungLogo.vue';
import BaseIcon from '../atoms/BaseIcon.vue';
import SearchBar from '../molecules/SearchBar.vue';
import MegaMenu from '../molecules/MegaMenu.vue';
import UserDropdown from '../molecules/UserDropdown.vue';

const mainNavItems = [
  { id: 'magaza', label: 'Mağaza' },
  { id: 'mobil', label: 'Mobil' },
  { id: 'tv', label: 'TV & AV' },
  { id: 'beyaz', label: 'Beyaz Eşyalar' },
  { id: 'monitor', label: 'Monitör & Depolama' },
  { id: 'giyilebilir', label: 'Giyilebilir Cihazlar' },
  { id: 'aksesuar', label: 'Aksesuarlar' }
];

const activeMenuId = ref(null);
const isUserMenuOpen = ref(false);

const showMenu = (id) => {
  activeMenuId.value = id;
};

const hideMenu = () => {
  activeMenuId.value = null;
};


let userMenuTimeout = null;

const showUserMenu = () => {
  clearTimeout(userMenuTimeout);
  isUserMenuOpen.value = true;
};

const delayedHideUserMenu = () => {
  clearTimeout(userMenuTimeout);
  userMenuTimeout = setTimeout(() => {
    isUserMenuOpen.value = false;
  }, 200); 
};
</script>

<template>
  <header
    class="site-header"
    :class="{ 
      'is-active': activeMenuId !== null && !isUserMenuOpen 
    }"
    @mouseleave="() => { if (!isUserMenuOpen) hideMenu(); }"
    >
    <div class="header-wrapper">

      <div class="utility-nav">
        <a href="#" class="util-link">Destek</a>
        <a href="#" class="util-link">Kurumsal için ↗</a>
      </div>

      <div class="header-inner">

        <div class="header-left">
          <a href="#" class="logo-link">
            <SamsungLogo width="110px" />
          </a>

          <nav class="nav-container">
            <a
              v-for="item in mainNavItems"
              :key="item.id"
              href="#"
              class="nav-item"
              :class="{ active: activeMenuId === item.id }"
              @mouseenter="showMenu(item.id)"
            >
              {{ item.label }}
            </a>
          </nav>
        </div>

        <div class="header-right">
          <div class="actions">

            <div class="search-box">
              <SearchBar />
            </div>

            <button class="icon-btn">
              <BaseIcon name="cart" size="24" />
            </button>

            <div
              class="user-menu-wrapper"
              @mouseenter="showUserMenu"
              @mouseleave="delayedHideUserMenu"
            >
              <button class="icon-btn">
                <BaseIcon name="user" size="24" />
              </button>

              <transition name="fade">
                <UserDropdown
                  v-show="isUserMenuOpen"
                  @mouseenter="showUserMenu"
                  @mouseleave="delayedHideUserMenu"
                />
              </transition>
            </div>

          </div>
        </div>

      </div>
    </div>

    <MegaMenu
      :isOpen="activeMenuId !== null && !isUserMenuOpen"
      :activeCategory="activeMenuId"
    />
  </header>
</template>

<style scoped>
.site-header {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 130px;
  z-index: 1000;
  font-family: 'Inter', sans-serif;
  background: transparent;
  color: #fff;
  transition: background-color 0.3s ease, color 0.3s ease;
  border-bottom: 1px solid transparent;
}

.site-header.is-active {
  background-color: #fff;
  color: #000;
  border-bottom: 1px solid #f0f0f0;
}

.header-wrapper {
  position: relative;
  max-width: 1640px;
  margin: 0 auto;
  height: 100%;
  padding: 0 75px;
}

.utility-nav {
  position: absolute;
  height: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
  right: 80px;
  top: 12px;
  z-index: 10;
}

.util-link {
  text-decoration: none;
  color: inherit;
  font-size: 14px;
  font-weight: 600;
}

.util-link:hover {
  opacity: 1;
  text-decoration: underline;
}

.header-inner {
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header-left {
  display: flex;
  align-items: center;
  gap: 48px;
  height: 100%;
}

.logo-link {
  display: flex;
  filter: brightness(0) invert(1);
  transition: filter 0.3s ease;
}

.site-header.is-active .logo-link {
  filter: none;
}

.nav-container {
  display: flex;
  gap: 8px;
  height: 100%;
  padding-top: 4px;
}

.nav-item {
  text-decoration: none;
  color: inherit;
  font-weight: 600;
  font-size: 15px;
  padding: 0 8px;
  display: flex;
  align-items: center;
  position: relative;
  height: 100%;
  transition: color 0.2s ease;
}

.site-header:not(.is-active) .nav-item {
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.4);
}

.site-header.is-active .nav-item:hover,
.site-header.is-active .nav-item.active {
  color: #1428a0;
}

.nav-item::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 4px;
  transform: scaleX(0);
}

.nav-item:hover::after,
.nav-item.active::after {
  transform: scaleX(1);
}

.site-header.is-active .nav-item::after {
  background-color: #1428a0;
}

.site-header:not(.is-active) .nav-item::after {
  background-color: #fff;
}

.header-right {
  display: flex;
  align-items: center;
  height: 100%;
}

.actions {
  display: flex;
  align-items: center;
  gap: 20px;
}

.icon-btn {
  background: none;
  border: none;
  cursor: pointer;
  padding: 2px;
  border-radius: 50%;
  display: flex;
  color: inherit;
  transition: transform 0.2s;
}

.user-menu-wrapper {
  position: relative;
  display: flex;
  align-items: center;
  height: 100%;
}

</style>
