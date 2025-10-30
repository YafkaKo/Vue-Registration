<script setup lang="ts">
const props = defineProps<{ step: string | string[] }>();

const getStepTitle = (step: string | string[]): string => {
  const stepValue = Array.isArray(step) ? step[0] : step;

  const titles: Record<string, string> = {
    "1": "Круто, что ты с нами!",
    "2": "Расскажи, про ВУЗ!",
    "3": "Продемонстрируй свои навыки!",
  };
  if (stepValue !== undefined && titles[stepValue] !== undefined)
    return titles[stepValue];
  return "Значение по умолчанию";
};
const getStepDescription = (step: string | string[]): string => {
  const stepValue = Array.isArray(step) ? step[0] : step;

  const description: Record<string, string> = {
    "1": "После этого шага тебе нужно будет указать информацию о вузе и добавить портфолио. Дождись проверки анкеты — и ты в деле!",
    "2": "Укажи, где ты учишься, на каком курсе и факультете. ",
    "3": "Добавь портфолио или отзывы клиентов. Это твой шанс выделиться и привлечь больше заказов.",
  };
  if (stepValue !== undefined && description[stepValue] !== undefined)
    return description[stepValue];
  return "Значение по умолчанию";
};
</script>

<template>
  <h2 class="title">
    {{ step ? getStepTitle(step) : "Значение по умолчанию" }}
  </h2>
  <p class="subtitle">
    {{ step ? getStepDescription(step) : "Значение по умолчанию" }}
  </p>
</template>

<style lang="scss" scoped>
.title {
  font-family: "Spoof Trial Bold";
  margin-bottom: 8px;
  font-size: 40px;
  @media (max-width: 768px) {
    font-size: 20px;
  }
}
.subtitle {
  font-size: 20px;
  line-height: 130%;
  margin-bottom: 32px;
  font-size: 20px;
  @media (max-width: 768px) {
    font-size: 16px;
    margin-bottom: 24px;
  }
}

</style>
