<template>
  <main class="s-main">
    <s-auth />
    <!-- <div class="s-authorization">
      <s-login v-if="formNameLogin" />
      <s-reg v-else />
      <span class="s-authorization__text">или</span>
      <button class="s-authorization__button" @click="checkForm">{{ formNameLogin ? 'Регистрация' : 'Войти' }}</button>
    </div> -->
  </main>
</template>

<!-- <script setup>
let formNameLogin = ref(true);

const checkForm = () => (formNameLogin.value = !formNameLogin.value);
</script> -->
