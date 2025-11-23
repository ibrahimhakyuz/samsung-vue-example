<script setup>
import BaseIcon from '../atoms/BaseIcon.vue';
</script>

<template>
  <div class="search-molecule">
    <button class="search-btn">
      <BaseIcon name="search" size="20" />
    </button>
    <input type="text" placeholder="Ara" class="search-input" />

  </div>
</template>

<style scoped>
.search-molecule {
  display: flex;
  align-items: center;
  background-color: rgba(247, 247, 247, 0.2);
  border-radius: 30px;
  padding: 7px 10px;
  width: 100%;
  max-width: 150px;
  gap: 5px;
}

.search-input {
  border: none;
  background: transparent;
  flex-grow: 1;
  outline: none;
  font-size: 14px;
  padding: 5px;
}

.search-btn {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
  display: flex;
  align-items: center;
}
</style>