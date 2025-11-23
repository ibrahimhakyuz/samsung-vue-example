<script setup>
import { ref } from 'vue';
import BaseButton from '@/components/atoms/BaseButton.vue';

const form = ref({
  email: '',
  password: '',
  confirmPassword: '',
  name: '',
  surname: '',
  day: '',
  month: '',
  year: ''
});

const showPassword = ref(false);
const showConfirmPassword = ref(false);
</script>

<template>
  <div class="page-wrapper">
    <div class="register-container">
      <h2 class="auth-title">Samsung hesabınızı oluşturun</h2>
      
      <form @submit.prevent class="auth-form">
        
        <div class="input-group">
          <input type="email" id="reg-email" v-model="form.email" required placeholder=" " />
          <label for="reg-email">E-posta</label>
        </div>

        <div class="input-group">
          <input 
            :type="showPassword ? 'text' : 'password'" 
            id="reg-pass" 
            v-model="form.password" 
            required 
            placeholder=" " 
          />
          <label for="reg-pass">Parola</label>
          <button type="button" class="eye-btn" @click="showPassword = !showPassword">
            <svg v-if="!showPassword" viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round" class="feather feather-eye-off"><path d="M17.94 17.94A10.07 10.07 0 0 1 12 20c-7 0-11-8-11-8a18.45 18.45 0 0 1 5.06-5.94M9.9 4.24A9.12 9.12 0 0 1 12 4c7 0 11 8 11 8a18.5 18.5 0 0 1-2.16 3.19m-6.72-1.07a3 3 0 1 1-4.24-4.24"></path><line x1="1" y1="1" x2="23" y2="23"></line></svg>
            <svg v-else viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round" class="feather feather-eye"><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path><circle cx="12" cy="12" r="3"></circle></svg>
          </button>
        </div>

        <div class="input-group">
          <input 
            :type="showConfirmPassword ? 'text' : 'password'" 
            id="reg-confirm-pass" 
            v-model="form.confirmPassword" 
            required 
            placeholder=" " 
          />
          <label for="reg-confirm-pass">Şifreyi onayla</label>
           <button type="button" class="eye-btn" @click="showConfirmPassword = !showConfirmPassword">
            <svg v-if="!showConfirmPassword" viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round" class="feather feather-eye-off"><path d="M17.94 17.94A10.07 10.07 0 0 1 12 20c-7 0-11-8-11-8a18.45 18.45 0 0 1 5.06-5.94M9.9 4.24A9.12 9.12 0 0 1 12 4c7 0 11 8 11 8a18.5 18.5 0 0 1-2.16 3.19m-6.72-1.07a3 3 0 1 1-4.24-4.24"></path><line x1="1" y1="1" x2="23" y2="23"></line></svg>
            <svg v-else viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round" class="feather feather-eye"><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path><circle cx="12" cy="12" r="3"></circle></svg>
          </button>
        </div>

        <div class="input-group">
          <input type="text" id="reg-name" v-model="form.name" required placeholder=" " />
          <label for="reg-name">Ad</label>
        </div>

        <div class="input-group">
          <input type="text" id="reg-surname" v-model="form.surname" required placeholder=" " />
          <label for="reg-surname">Soyadı</label>
        </div>

        <div class="date-row">
          <div class="input-group date-item">
            <input type="text" id="dob-day" v-model="form.day" placeholder=" " />
            <label for="dob-day">Gün</label>
          </div>
          
          <div class="input-group date-item">
            <select id="dob-month" v-model="form.month" class="custom-select">
              <option value="" disabled selected hidden></option> <option v-for="m in 12" :key="m" :value="m">{{ m }}. Ay</option>
            </select>
            <label for="dob-month" class="select-label">Ay</label>
            <span class="select-arrow">▼</span>
          </div>

          <div class="input-group date-item">
            <input type="text" id="dob-year" v-model="form.year" placeholder=" " />
            <label for="dob-year">Yıl</label>
          </div>
        </div>

        <div class="button-row">
          <BaseButton variant="dark-gray" class="btn-half">Geri</BaseButton>
          <BaseButton variant="blue" class="btn-half">Sonraki</BaseButton>
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

.register-container {
  width: 100%;
  max-width: 480px;
  padding: 40px 30px;
  background: #121212;
  border-radius: 26px;
  text-align: left; 
}

.auth-title {
  font-size: 22px;
  color: #fff;
  margin-bottom: 30px;
  font-weight: 400;
}

.auth-form {
  display: flex;
  flex-direction: column;
  gap: 15px; 
}

.input-group {
  position: relative;
  width: 100%;
  margin-bottom: 5px;
}

.input-group input, 
.custom-select {
  width: 100%;
  padding: 10px 0;
  font-size: 16px;
  color: #fff;
  background: transparent;
  border: none;
  border-bottom: 1px solid #555;
  outline: none;
  transition: border-color 0.3s;
  border-radius: 0; 
}

.input-group label {
  position: absolute;
  top: 10px;
  left: 0;
  font-size: 16px;
  color: #777;
  pointer-events: none;
  transition: 0.3s ease all;
}

.input-group input:focus,
.input-group input:not(:placeholder-shown),
.custom-select:focus,
.custom-select:not([value=""]) {
  border-bottom: 2px solid #007aff;
}

.input-group input:focus + label,
.input-group input:not(:placeholder-shown) + label,
.custom-select:focus + .select-label,
.custom-select:not([value=""]) + .select-label {
  top: -12px;
  font-size: 12px;
  color: #007aff;
}

.eye-btn {
  position: absolute;
  right: 0;
  top: 5px;
  background: none;
  border: none;
  color: #777;
  cursor: pointer;
  padding: 5px;
}

.date-row {
  display: flex;
  gap: 20px; 
  margin-top: 10px;
}

.date-item {
  flex: 1; 
}

.custom-select {
  appearance: none; 
  cursor: pointer;
}
.select-arrow {
  position: absolute;
  right: 0;
  top: 15px;
  font-size: 10px;
  color: #777;
  pointer-events: none;
}

.button-row {
  display: flex;
  gap: 15px;
  margin-top: 40px;
}

.btn-half {
  flex: 1; 
  border-radius: 25px; 
}
</style>