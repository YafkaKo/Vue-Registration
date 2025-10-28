<script setup lang="ts">
import AccentButton from "../ui/AccentButton.vue";

const props = defineProps<{ step: string | string[] }>();
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
  <div class="buttons">
    <nuxt-link
      v-if="step !== '3'"
      :to="step === '1' ? '/registration/2' : '/registration/3'"
      ><AccentButton text="Продолжить"
    /></nuxt-link>
    <nuxt-link v-if="step === '3'" to="/gift"
      ><AccentButton text="Готово"
    /></nuxt-link>
    <nuxt-link to="/contact/telegram"
      ><button v-if="step === '1'" class="bottom-button">
        Войти в аккаунт
      </button></nuxt-link
    >
    <nuxt-link @click.prevent="goBack"
      ><button v-if="step !== '1'" class="bottom-button">
        Назад
      </button></nuxt-link
    >
  </div>
</template>

<style lang="scss" scoped>
.buttons {
  font-family: "PP Neue Montreal Medium", sans-serif;
  font-size: 20px;
  line-height: 130%;
  .bottom-button {
    color: $accent-violet;
    padding: 20px 0;
    width: 100%;
    @media(max-width: 768px){
    font-size: 16px;
    padding: 12px 0;
  }
  }
}
</style>
