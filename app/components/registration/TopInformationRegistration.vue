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
  <div class="steps">
    <div class="step active">01</div>
    <div :class="step === '2' || step === '3' ? 'step active' : 'step'">02</div>
    <div :class="step === '3' ? 'step active' : 'step'">03</div>
  </div>
</template>

<style lang="scss" scoped>
.title {
  font-family: "Spoof Trial Bold";
  margin-bottom: 8px;
  font-size: 40px;
}
.subtitle {
  font-size: 20px;
  line-height: 130%;
  margin-bottom: 32px;
  font-size: 20px;
}

.steps {
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: "Spoof Trial Bold";
  font-size: 40px;
  line-height: 130%;
  gap: 56px;
  margin-bottom: 32px;
  .step.active {
    color: $accent-violet;
  }
  .step {
    color: $teriary-dark;
    position: relative;
  }
  .step:not(:last-child)::after {
    content: "";
    position: absolute;
    right: -8px;
    top: 50%;
    transform: translateY(-50%) translateX(100%);
    width: 40px;
    height: 1px;
    background: $teriary-dark;
    z-index: 1;
  }
}
</style>
