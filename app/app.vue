<script setup lang="ts">
import HeaderMain from "./components/layout/HeaderMain.vue";
import FooterMain from "./components/layout/FooterMain.vue";
</script>

<template>
  <div class="wrapper">
    <HeaderMain />
    <main>
      <NuxtPage />
    </main>
    <FooterMain />
  </div>
</template>

<style lang="scss">
body {
  background-color: $primary-dark;
  background-image: url("@/assets/images/Background_img.jpg");
  background-repeat: no-repeat;
  background-size: cover;

  color: #171717;
  font-family: "PP Neue Montreal Book", sans-serif;
}

.wrapper {
  max-width: 1440px;
  padding: 0 20px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  min-height: 100vh;
  main {
    flex-grow: 1;
    margin: 24px 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}

input,
textarea {
  border: 1px solid $teriary-dark;
  border-radius: 12px;
  padding: 12px 16px;
  font-family: "PP Neue Montreal Medium", sans-serif;
  line-height: 130%;
  font-size: 16px;
  width: 100%;
  @media(max-width: 768px){
    font-size: 14px;
    padding: 8px 12px;
      }
  &::placeholder {
    opacity: 50%;
  }
}

.input-with-icons-container {
  width: 100%;
  position: relative;
  button {
    position: absolute;
    top: 14px;
    right: 16px;
  }
  input,
  label {
    padding: 12px 48px 12px 16px;
  }
  .btn-img-galochka-reverse {
    transform: rotate(180deg);
  }
  .suggestions-list {
    position: absolute;
    bottom: auto;
    width: 100%;
    z-index: 100;
  }
  .suggestion-item {
    background: #fff;
    padding: 6px 12px;
    cursor: pointer;
    border: 1px solid $teriary-dark;
    border-radius: 12px;
    font-family: "PP Neue Montreal Medium", sans-serif;
    line-height: 130%;
    font-size: 16px;
  }
}

.inputs-sharing {
  display: flex;
  gap: 16px;
  @media(max-width: 500px){
    flex-wrap: wrap;
      }
}
</style>
