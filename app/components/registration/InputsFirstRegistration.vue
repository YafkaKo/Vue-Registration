<script setup lang="ts">
import InputWithPassword from '../ui/InputWithPassword.vue';
import InputWithSuggestions from '../ui/InputWithSuggestions.vue'

    const suggestions = [
      'Москва',
      'Санкт-Петербург',
      'Новосибирск',
    ]
</script>

<template>
  <div class="inputs">
        <div class="inputs-sharing">
          <InputWithSuggestions :suggestions="suggestions" name="NickName" id="NickName" placeholder="NickName*" />
          <InputWithSuggestions :suggestions="suggestions" name="Name" id="Name" placeholder="Name*" />
              </div>
          <input type="text" name="Female" id="Female" placeholder="Фамилия*"></input>
          <input type="email" name="Email" id="Email" placeholder="Email*">
          <InputWithPassword name="Password" id="Password" placeholder="Пароль*" />
          <InputWithPassword name="PasswordRepeat" id="PasswordRepeat" placeholder="Повторите пароль*" />
        </div>
</template>

<style lang="scss" scoped>

.inputs{
    margin-bottom: 24px;
        input{
      border: 1px solid $teriary-dark;
      border-radius: 12px;
      padding: 12px 16px;
      font-family: 'PP Neue Montreal Medium', sans-serif;
      line-height: 130%;
      font-size: 16px;
      width: 100%;
      &::placeholder{
        opacity: 50%;

      }

    }
    .inputs-sharing{
      display: flex;
      gap: 16px;
      width: 100%;
    }

    display: flex;
    flex-direction: column;
    gap: 16px;
  }
</style>