<script lang="ts" setup>
const props = defineProps<{ step: string | string[] }>()
</script>

<template>
    <div class="steps">
    <div class="step active">01</div>
    <div :class="step === '2' || step === '3' ? 'step active' : 'step'">02</div>
    <div :class="step === '3' ? 'step active' : 'step'">03</div>
  </div>
</template>

<style lang="scss" scoped>
.steps {
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: "Spoof Trial Bold";
  font-size: 40px;
  line-height: 130%;
  gap: 56px;
  margin-bottom: 32px;
  @media(max-width: 768px){
    font-size: 32px;
    margin-bottom: 24px;
    gap: 40px
      }
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
    @media(max-width: 768px){
      width: 24px;

    }
  }
}</style>