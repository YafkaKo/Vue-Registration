<script setup lang="ts">
import InputWithFile from '../ui/InputWithFile.vue';
import InputWithSuggestions from '../ui/InputWithSuggestions.vue';


const suggestions = ["Москва", "Санкт-Петербург", "Новосибирск"];
</script>

<template>
  <div class="inputs">
    <InputWithSuggestions
      :suggestions="suggestions"
      name="Disciplina"
      id="Disciplina"
      placeholder="Дисциплина"
    />
    <textarea name="About" id="About" placeholder="О себе"></textarea>
    <InputWithFile
      name="Feedback"
      id="Feedback"
      placeholder="Отзывы заказчиков"
      label="Прикрепи фото студенческого хорошего качества в формате PNG или JPEG"
    />
    <InputWithFile
      name="Portfolio"
      id="Portfolio"
      placeholder="Портфолио"
      label="Прикрепи фото студенческого хорошего качества в формате PNG или JPEG"
    />
  </div>
</template>

<style lang="scss" scoped>
textarea {
  resize: none;
  min-height: 120px;
  max-height: 150px;
  text-align: start;
}
</style>
