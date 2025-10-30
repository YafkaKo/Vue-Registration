<script lang="ts" setup>
import type { Animal } from "~/pages/slider.vue";

const props = defineProps<{ animal: Animal, currentAnimal: number }>();
</script>
<template>
  <div
    :class="currentAnimal === props.animal.id ? 'slider-item active': 'slider-item'"
    :key="props.animal.id"
    :style="`background-image: url(${props.animal.image});`
    "
  >
    <h2 class="slider-item-title">{{ props.animal.name }}</h2>
    <p class="slider-item-subtitle">
      {{ props.animal.description }}
    </p>
    <NuxtLink to="/registration" class="slider-item-link">Explore</NuxtLink>
  </div>
</template>

<style lang="scss" scoped>
.slider {
  &-item {
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    color: #fff;
    padding: 40px 40px;
    gap: 12px;
    width: 400px;
    height: 400px;
    display: flex;
    flex-direction: column;
    justify-content: end;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
    transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
    position: absolute;
    cursor: pointer;
  }
  &-item-title {
    font-size: 32px;
    font-weight: bold;
  }
  &-item-subtitle {
    font-size: 16px;
  }
  &-item-link {
    font-size: 24px;
    font-weight: bold;
    padding: 6px 24px;
    background-color: #fff;
    color: black;
    border-radius: 12px;
    width: fit-content;
  }
}
</style>
