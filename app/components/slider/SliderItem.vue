<script lang="ts" setup>
import type { Animal } from "~/pages/slider.vue";
interface Props {
  animal: Animal
  currentAnimal: number
  dragOffset?: number
  isDragging?: boolean
  slideStyle?: any
}
const props = withDefaults(defineProps<Props>(),{dragOffset: 0,
  isDragging: false,
  slideStyle: () => ({})});

const mergedStyles = computed(() => ({
  ...props.slideStyle,
  transform: `${props.slideStyle.transform || ''} translateX(${props.dragOffset}px)`,
  transition: props.isDragging ? 'none' : 'transform 0.6s cubic-bezier(0.4, 0, 0.2, 1)',
  backgroundImage: `url(${props.animal.image})`
}))
</script>
<template>
  <div
    :class="currentAnimal === props.animal.id ? 'slider-item active unselectable': 'slider-item unselectable'"
    :key="props.animal.id"
      :style='mergedStyles'
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
.unselectable {
  -webkit-touch-callout: none; /* iOS Safari */
  -webkit-user-select: none;   /* Chrome/Safari/Opera */
  -khtml-user-select: none;    /* Konqueror */
  -moz-user-select: none;      /* Firefox */
  -ms-user-select: none;       /* Internet Explorer/Edge */
  user-select: none;           /* Non-prefixed version, currently
                                  not supported by any browser */
}
</style>
