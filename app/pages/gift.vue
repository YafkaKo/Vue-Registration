<script setup lang="ts">
import AccentButton from "~/components/ui/AccentButton.vue";
</script>

<template>
  <div class="gift-container">
    <button class="close-button">
      <img src="@/assets/images/close.svg" alt="close" />
    </button>
    <h2 class="gift-title">🎁 Подарок от друга!</h2>
    <p class="gift-subtitle">
      Зарегистрируйся по ссылке друга и получи от 300 бонусов на счёт! Это твой
      шанс начать с приятного бонуса
    </p>
    <h3 class="gift-list-title">Что можно сделать?</h3>
    <ol class="gift-list">
      <li class="gift-list-item">Перейди по ссылке — получи её от друга.</li>
      <li class="gift-list-item">Зарегистрируйся — это займёт пару минут.</li>
      <li class="gift-list-item">
        Получи бонусы — от 300 единиц, которые можно потратить на заказы или
        вывести.
      </li>
    </ol>
    <nuxt-link to="/application" class="gift-link"
      ><AccentButton text="Круто"
    /></nuxt-link>
  </div>
</template>

<style lang="scss" scoped>
.gift-container {
  width: 542px;
  margin: 0 auto;
  background-color: #fff;
  border-radius: 24px;
  padding: 45.5px 24px;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: start;
  text-align: start;
  @media(max-width: 768px){
    padding: 48px 16px;
      }
  .close-button {
    position: absolute;
    top: 10px;
    right: 12px;
    @media(max-width: 768px){
      top: 20px;
      right: 16px;
    }
  }
  .gift-title {
    font-family: "Spoof Trial Medium";
    font-size: 28px;
    margin-bottom: 4px;
    @media(max-width: 500px){
    font-size: 18px;
      }
  }
  .gift-subtitle {
    font-size: 16px;
    color: $light-dark;
    margin-bottom: 32px;
    @media(max-width: 768px){
    margin-bottom: 24px;
      }
  }
  .gift-list-title {
    font-family: "Spoof Trial Bold";
    font-size: 20px;
    margin-bottom: 8px;
    @media(max-width: 768px){
      font-size: 16px;
                }
  }
  .gift-list {
    color: $light-dark;
    font-size: 16px;
    line-height: 130%;
    margin-bottom: 32px;
    @media(max-width: 768px){
    margin-bottom: 24px;
    font-size: 14px;
      }
  }
  .gift-link {
    width: 100%;
  }
}
</style>
