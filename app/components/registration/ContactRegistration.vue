<script setup lang="ts"></script>

<template>
  <div class="contact">
    <h3 class="contact-title">Укажи удобный способ связи</h3>
    <p class="contact-subtitle">
      Добавь Telegram или ВКонтакте. Мы напишем только в случае вопросов по
      заказу. Чем больше контактов, тем проще связаться!
    </p>
    <div class="social">
      <NuxtLink to="/contact/telegram" class="social-item tel"
        ><img
          src="@/assets/images/telegram.svg"
          alt="telegram"
          class="social-icon"
        />
        <p>Telegram</p>
        <div>+</div></NuxtLink
      >
      <NuxtLink to="/contact/vk" class="social-item vk"
        ><img src="@/assets/images/vk.svg" alt="vk" class="social-icon" />
        <p>ВКонтакте</p>
        <div>+</div></NuxtLink
      >
    </div>
  </div>
  <div class="policy">
    <input class="policy-input" type="checkbox" name="policy" id="policy" />
    <label for="policy"
      >Принимаю <NuxtLink to="/policy"
        >Пользовательское соглашение, политику конфиденциальности</NuxtLink
      > и <NuxtLink to="/policy"
        >политику использования файлов cookie.</NuxtLink
      ></label
    >
  </div>
</template>

<style lang="scss" scoped>
.contact {
  margin-bottom: 16px;
  .contact-title {
    font-family: "PP Neue Montreal Medium", sans-serif;

    font-size: 24px;
    line-height: 130%;
    margin-bottom: 8px;
  }
  .contact-subtitle {
    font-size: 16px;
    line-height: 130%;
    margin-bottom: 16px;
  }
  .social {
    display: flex;
    justify-content: space-between;
    @media(max-width: 768px){
      flex-wrap: wrap;
    }
    .social-item {
      &.tel {
        color: #29a9eb;
      }
      &.vk {
        color: #0077ff;
      }
      width: 100%;
      padding: 12px 24px;
      display: flex;
      align-items: center;
      gap: 10px;
      img {
        width: 24px;
        height: 24px;
      }
      p {
        font-family: "PP Neue Montreal Medium", sans-serif;
        font-size: 20px;
        line-height: 130%;
      }
      div {
        margin-left: auto;
        font-size: 24px;
      }
    }
  }
}
.policy {
  display: flex;
  align-items: start;
  gap: 8px;
  font-size: 14px;
  line-height: 130%;
  margin-bottom: 32px;
  a {
    color: $accent-violet;
  }
  .policy-input {
    min-width: 18px;
    min-height: 18px;
    max-width: 18px;
    max-height: 18px;
    border: 2px solid $teriary-dark;
  }
}
</style>
