<script setup lang="ts">
import { onMounted, onUnmounted, ref } from "vue";
import AccentButton from "~/components/ui/AccentButton.vue";

onMounted(() => {
  document.body.classList.add("special-page-active");
});

onUnmounted(() => {
  document.body.classList.remove("special-page-active");
});

const isSuccess = ref(false)
const setSuccess = () => {
  isSuccess.value = !isSuccess.value
}

let intervalId:any

onMounted(() => {
  intervalId = setInterval(setSuccess, 7000)
})

onUnmounted(() => {
  if (intervalId) {
    clearInterval(intervalId)
  }
})
</script>

<template>
  <div class="application">
    <h1 class="application-title">{{isSuccess ? '🎉 Регистрация завершена!' :'✨ Ты почти в команде!'}}</h1>
    <p class="application-subtitle"> {{isSuccess ? 'Анкета проверена — ты в StudY! Можешь пройти инструкцию или начать работать сразу. Ты справишься!':'Анкета отправлена — осталось дождаться подтверждения. Скоро ты сможешь начать пользоваться всеми возможностями платформы! '}}</p>

    <div :class="isSuccess ? 'application-way success' : 'application-way'">
  <div class="way-item">
      <div class="way-item-box">
      <img class="way-send" src="@/assets/images/userid.svg" alt="user"></img>
      <div class="arrow"></div>
      </div>
      </div>
<div class="way-item">
<div class="way-item-box">
      <img class="way-check" src="@/assets/images/message.svg" alt="send"></img>
      <div class="arrow"></div>
</div>
    </div>
      <div class="way-item">
        <div class="way-item-box">
      <img class="way-success" src="@/assets/images/success.svg" alt="success"></img>
        </div>
    </div>
    </div>
    <div class="zagluxhka"></div>
    <div v-if="isSuccess" class="bottom-buttons">
      <AccentButton text="Показать инструкцию"/>
      <button class="button-white">Я сам всё освою</button>
    </div>
  </div>

</template>

<style lang="scss" scoped>
body.special-page-active {
  background-image: none;
}


.application{
  flex-grow: 1;
  height: 100%;
  max-width: 828px;
  width: 100%;
  padding: 48px 60px;
  color: #fff;
  text-align: center;
  display: flex;
  flex-direction: column;
  min-height: -webkit-fill-available;
  @media(max-width: 768px){
    padding: 0;
      }
  .zagluxhka{
    flex-grow: 1;
  }
  &-title{
font-family: 'Spoof Trial Medium';
    font-size: 40px;
    margin-bottom: 8px;
    @media(max-width: 768px){
    font-size: 18px;
      }
  }
  &-subtitle{
    font-size: 20px;
    margin-bottom: 48px;
    @media(max-width: 768px){
    margin-bottom: 32px;
    font-size: 14px;
      }
  }
}
.application-way{
    display: grid;
  // grid-template-columns: 345px 243px 40px;
  grid-template-columns: 50% auto 40px;
  width: calc(100% - 48px - 32px);
  gap: 16px;
  font-family: 'PP Neue Montreal Medium';
  margin: 0 auto;
  @media(max-width: 768px){
      grid-template-columns: 1fr;
      grid-template-rows: 80px 40px;
                }
  .way-item{
    line-height: 100%;
        &-box{
      display: flex;
      align-items: center;
      justify-content: center;
      width: 40px;
      height: 40px;
      border-radius: 28px;
      background-color: $secondary-dark;
    }
        &:first-child{
          .way-item-box{
            background-color: $accent-violet;;
          }
          position: relative;
          .way-item-box::before{
            position: absolute;
            content: '';
            z-index: 0;
            width: calc(100% - 37px);
            height: 4px;
            background-color: $accent-violet;
            right: 0;
            top: calc(50% - 2px);
            border-radius: 5px;
            @media(max-width: 768px){
              width: 4px;
              height: 43px;
              bottom: 0;
              left: 18px;
              top: auto;
              right: 0;
              }
          }

          .way-item-box::after{
            position: absolute;
            content: 'Анкета отправлена';

            left: 56px;
            width: max-content;
            padding: 4px 8px;
            background-color: $accent-violet;
            border-radius: 16px;
            z-index: 2;
          }
        }
        &:first-child::before,&:first-child::after,&:nth-child(2)::before,&:nth-child(2)::after{
          content: '';
        position: absolute;
        top: 0;
        right: -3px;
        width: 25px;
        height: 4px;
        background: $accent-violet;
        border-radius: 4px; /* Скругление углов */
        transform: translateY(-50%) rotate(-45deg);
        top: calc(50% + 8px);
        @media(max-width: 768px){
          top: auto;
          right: auto;
          bottom: 5px;
          left: 0px;
          transform: rotate(45deg);
        }
        }
        &:first-child::after,&:nth-child(2)::after{
        transform: translateY(-50%) rotate(45deg);
        top: calc(50% - 8px);
        @media(max-width: 768px){
          top: auto;
          right: auto;
          left: 15px;
          transform: rotate(-45deg);
        }
        }

        &:nth-child(2){
          &::before,&::after{
            background: $secondary-dark;
          }
        .way-item-box::before{
            position: absolute;
            content: '';
            z-index: 0;
            width: calc(100% - 37px);
            height: 4px;
            background-color: $secondary-dark;
            right: 0;
            top: calc(50% - 2px);
            border-radius: 5px;
          }
        }
  }
  .way-item:nth-child(2){
    position: relative;
    .way-item-box::after{
      position: absolute;
      content: 'Проверка';
      left: 56px;

      width: max-content;
      padding: 4px 8px;
      background-color: $secondary-dark;
      border-radius: 16px;
      z-index: 2;
    }
  }
}

@media(max-width: 768px){
  .way-item{
    &:last-child{
display: none;
    }
    &:nth-child(2)::after,&:nth-child(2)::before,&:nth-child(2) .way-item-box::before{
      display: none;
    }

  }
}

.application-way.success{
  .way-item:nth-child(2) .way-item-box,.way-item:nth-child(2)
  .way-item-box::before,.way-item:nth-child(2)
  .way-item-box::after,.way-item:nth-child(2)::after,
  .way-item:nth-child(2)::before,
  .way-item:last-child .way-item-box{
    background: $accent-violet;
  }
  @media(max-width: 768px){
    .way-item:last-child{
      display: block;
      .way-item-box::before{
      position: absolute;
      content: 'Принята';
      left: 118px;

      width: max-content;
      padding: 4px 8px;
      background-color: $accent-violet;
      border-radius: 16px;
      z-index: 2;
      }
    }
          .way-item:nth-child(2){
            display: none;

  }
        }
}

.bottom-buttons{
  margin: 0 auto;
  display: flex;
  gap: 30px;
  width: calc(256px + 256px + 30px);
  @media(max-width: 768px){
      flex-direction: column;
      width: 100%;
    }
  .button-white{
  font-family: "PP Neue Montreal Medium", sans-serif;
  font-size: 20px;
  line-height: 130%;
  width: 100%;
  background-color: #fff;
  border-radius: 12px;
  padding: 12px 0;
  color: $accent-violet;
    @media(max-width: 768px){
    font-size: 16px;
      }
  }
}
</style>
