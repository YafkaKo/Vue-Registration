<script setup lang="ts">
import { useRoute } from "vue-router";
const route = useRoute();
</script>

<template>
  <header>
    <NuxtLink to="/" class="logo">LOGO</NuxtLink>
    <NuxtLink
      v-if="route.path !== '/vk' && route.path !== '/telegram'"
      to="/gift"
      class="button-gift"
    >
      <img src="@/assets/images/gift.svg" alt="gift svg" /><span>Подарок от
      друга</span></NuxtLink
    >
  </header>
</template>

<style lang="scss" scoped>
header {
  padding: 20px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  .logo {
    text-transform: uppercase;
    font-family: "Sora";
    font-weight: 600;
    font-size: 36px;
    color: #fff;
  }
  .button-gift {
    background-color: #caf272;
    padding: 12px 32px;
    font-family: "PP Neue Montreal Medium";
    font-weight: 500;
    font-size: 20px;
    display: flex;
    justify-content: space-between;
    gap: 10px;
    border-radius: 12px;
    align-items: center;
    img {
      width: 24px;
      height: 24px;
    }
  }
}

@media(max-width: 768px){
  header{
    padding: 10px 0;
    .logo{
      font-size: 32px;
    }
    .button-gift{
      padding: 10px 12px;
      font-size: 16px;
      gap: 5px;
      span{
        display: none;
      }
    }
  }
}
</style>
