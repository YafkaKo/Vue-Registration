<script setup lang="ts">
import telegramIcon from "@/assets/images/telegram.svg";
import vkIcon from "@/assets/images/vk.svg";
import { useRouter } from "vue-router";
import AccentButton from "../ui/AccentButton.vue";

const props = defineProps<{ title: string }>();

const router = useRouter();

const goBack = () => {
  if (window.history.state.back) {
    router.back();
  } else {
    router.push("/");
  }
};
</script>

<template>
  <div class="add-contact-modal">
    <button class="button-back" @click.prevent="goBack">
      <img src="@/assets/images/arrow.svg" alt="" />
    </button>
    <img
      class="contact-logo"
      :src="title === 'Telegram' ? telegramIcon : vkIcon"
      alt="Logo"
    />
    <h2 class="contact-title">{{ title }}</h2>
    <p class="contact-subtitle">Добавить контакт</p>
    <input class="contact-input" type="text" placeholder="Ссылка на профиль" />
    <AccentButton class="contact-button" text="Сохранить" />
  </div>
</template>

<style lang="scss" scoped>
.add-contact-modal {
  margin-bottom: 24px;
  width: 542px;
  margin: 0 auto;
  background-color: #fff;
  border-radius: 24px;
  padding: 48px 24px;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  .button-back {
    position: absolute;
    top: 20px;
    left: 24px;
  }
  .contact-logo {
    width: 56px;
    height: 56px;
    margin-bottom: 16px;
  }
  .contact-title {
    font-family: "PP Neue Montreal Medium";
    font-size: 24px;
    margin-bottom: 8px;
  }
  .contact-subtitle {
    font-size: 16px;
    margin-bottom: 32px;
  }
  .contact-input {
    margin-bottom: 32px;
  }
}
</style>
