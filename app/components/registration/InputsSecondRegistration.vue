<script setup lang="ts">
import InputWithFile from "../ui/InputWithFile.vue";
import InputWithSuggestions from "../ui/InputWithSuggestions.vue";

const suggestions = ["Москва", "Санкт-Петербург", "Новосибирск"];
</script>

<template>
  <div class="inputs">
    <InputWithSuggestions
      :suggestions="suggestions"
      name="VUZ"
      id="VUZ"
      placeholder="ВУЗ"
    />
    <InputWithSuggestions
      :suggestions="suggestions"
      name="Faculty"
      id="Faculty"
      placeholder="Факультет"
    />
    <InputWithSuggestions
      :suggestions="suggestions"
      name="Cafedra"
      id="Cafedra"
      placeholder="Кафедра"
    />
    <div class="inputs-sharing">
      <InputWithSuggestions
        :suggestions="suggestions"
        name="Course"
        id="Course"
        placeholder="Курс"
      />
      <InputWithSuggestions
        :suggestions="suggestions"
        name="Level"
        id="Level"
        placeholder="Уровень образования"
      />
    </div>
    <InputWithFile
      name="StudyBook"
      id="StudyBook"
      placeholder="Студенческий"
      label="Прикрепи фото студенческого хорошего качества в формате PNG или JPEG"
    />
  </div>
</template>

<style lang="scss" scoped></style>
