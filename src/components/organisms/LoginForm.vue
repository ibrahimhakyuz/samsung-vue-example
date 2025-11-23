<script setup>
import { ref } from 'vue';
import BaseButton from '@/components/atoms/BaseButton.vue'; 

const email = ref('');
const rememberId = ref(false);
</script>

<template>
  <div class="page-wrapper">
    <div class="login-container">
      <h2>Bir hesap. Tüm cihazlar.<br>Size özel.</h2>
      <p>Başlamak için oturum açın</p>

      <form @submit.prevent class="login-form">
        
        <div class="input-group">
          <input 
            type="email" 
            id="email" 
            v-model="email" 
            required
            placeholder=" "
          />
          <label for="email">E-posta adresi</label>
        </div>

        <div class="checkbox-container">
          <label class="custom-checkbox">
            <input type="checkbox" v-model="rememberId">
            <span class="checkmark"></span>
            ID'mi hatırla
          </label>
        </div>

        <div class="actions">
          
          <BaseButton variant="blue" block type="submit">
            Sonraki
          </BaseButton>
          
          <div class="links">
            <a href="#">ID Bul</a>
            <a href="#">Hesap oluştur</a>
          </div>

          <BaseButton 
            variant="dark-gray" 
            block 
            type="button"
          >
            <div class="g-icon-wrapper">
              <svg viewBox="0 0 24 24" width="18" height="18" xmlns="http://www.w3.org/2000/svg">
                <g transform="matrix(1, 0, 0, 1, 27.009001, -39.238998)">
                  <path fill="#4285F4" d="M -3.264 51.509 C -3.264 50.719 -3.334 49.969 -3.454 49.239 L -14.754 49.239 L -14.754 53.749 L -8.284 53.749 C -8.574 55.229 -9.424 56.479 -10.684 57.329 L -10.684 60.329 L -6.824 60.329 C -4.564 58.239 -3.264 55.159 -3.264 51.509 Z" />
                  <path fill="#34A853" d="M -14.754 63.239 C -11.514 63.239 -8.804 62.159 -6.824 60.329 L -10.684 57.329 C -11.764 58.049 -13.134 58.489 -14.754 58.489 C -17.884 58.489 -20.534 56.379 -21.484 53.529 L -25.464 53.529 L -25.464 56.619 C -23.494 60.539 -19.444 63.239 -14.754 63.239 Z" />
                  <path fill="#FBBC05" d="M -21.484 53.529 C -21.734 52.809 -21.864 52.039 -21.864 51.239 C -21.864 50.439 -21.734 49.669 -21.484 48.949 L -21.484 45.859 L -25.464 45.859 C -26.284 47.479 -26.754 49.299 -26.754 51.239 C -26.754 53.179 -26.284 54.999 -25.464 56.619 L -21.484 53.529 Z" />
                  <path fill="#EA4335" d="M -14.754 43.989 C -12.984 43.989 -11.404 44.599 -10.154 45.799 L -6.734 42.379 C -8.804 40.439 -11.514 39.239 -14.754 39.239 C -19.444 39.239 -23.494 41.939 -25.464 45.859 L -21.484 48.949 C -20.534 46.099 -17.884 43.989 -14.754 43.989 Z" />
                </g>
              </svg>
            </div>
            Google ile oturum aç
          </BaseButton>

        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>
*, *::before, *::after {
  box-sizing: border-box;
}

.page-wrapper {
  background-color: #000;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Inter', sans-serif;
}

.login-container {
  width: 100%;
  max-width: 490px; 
  padding: 48px 20px; 
  background: #121212;
  border-radius: 26px;
  text-align: center;
}

.login-form {
  width: 100%;
  max-width: 300px; 
  margin: 0 auto;  
  text-align: left;
}

h2 { 
  font-size: 22px; 
  margin-bottom: 15px; 
  color: #fff; 
  font-weight: 500;
}

p { 
  color: #dedddd; 
  margin-bottom: 60px; 
  font-size: 14px; 
}

.input-group {
  position: relative;
  margin-bottom: 10px;
  width: 100%; 
}

.input-group input {
  width: 100%;
  padding: 6px 0;
  font-size: 16px;
  color: #fff;
  background: transparent;
  border: none;
  border-bottom: 1px solid #555;
  outline: none;
  transition: border-color 0.3s;
}

.input-group label {
  position: absolute;
  top: 10px;
  left: 0; 
  font-size: 13px;
  color: #777;
  pointer-events: none;
  transition: 0.3s ease all;
}

.input-group input:focus,
.input-group input:not(:placeholder-shown) {
  border-bottom: 2px solid #007aff;
}

.input-group input:focus + label,
.input-group input:not(:placeholder-shown) + label {
  top: -12px;
  font-size: 13px;
  color: #007aff;
}

.checkbox-container {
  display: flex;
  justify-content: flex-start;
  margin-bottom: 30px;
  width: 100%;
}

.custom-checkbox {
  display: flex;
  align-items: center;
  color: #fff;
  font-size: 12px;
  cursor: pointer;
  position: relative;
  padding-left: 30px;
}

.custom-checkbox input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
}

.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 20px;
  width: 20px;
  background-color: transparent;
  border: 1px solid #777;
  border-radius: 50%;
}

.custom-checkbox:hover input ~ .checkmark {
  border-color: #aaa;
}

.custom-checkbox input:checked ~ .checkmark {
  background-color: #007aff;
  border-color: #007aff;
}

.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

.custom-checkbox input:checked ~ .checkmark:after {
  display: block;
}

.custom-checkbox .checkmark:after {
  left: 7px;
  top: 3px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
}

.actions {
  display: flex;
  flex-direction: column;
  gap: 20px;
  width: 100%;
}

.links {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 12px;
  margin: 5px 0 10px 0;
  width: 100%;
}

.links a { 
  color: #777; 
  text-decoration: underline; 
  font-size: 14px; 
  font-weight: 500;
  text-decoration-color: #777;
  text-underline-offset: 4px;
}

.g-icon-wrapper {
  background: #fff;
  border-radius: 50%;
  width: 20px;
  height: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2px;
}
</style>