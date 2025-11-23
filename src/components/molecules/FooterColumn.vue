<script setup>
defineProps({
  title: String,
  links: Array
});
</script>

<template>
  <div class="footer-column">
    <h4 class="column-title">{{ title }}</h4>
    <ul class="link-list">
      <li v-for="(link, index) in links" :key="index">
        <a href="#">
          {{ link }}
        </a>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.footer-column {
  min-width: 140px;
  margin-bottom: 30px;
  padding:20px;
  border-top: 1px solid #e0e0e0;
  border-bottom: 1px solid #e0e0e0;
}

.column-title {
  font-size: 16px; 
  font-weight: 700;
  margin: 0 0 20px 0; 
  color: #000;
}

.link-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.link-list li {
  margin-bottom: 12px; 
}

.link-list a {
  text-decoration: none;
  color: #232323;
  font-size: 13px;
  line-height: 1.4;
  transition: color 0.2s;
}

.link-list a:hover {
  color: #1428a0;
  text-decoration: underline;
}
</style>