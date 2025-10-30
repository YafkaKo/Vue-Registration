<script setup lang="ts">
import { transition } from "@vueuse/core";
import { useRoute } from "vue-router";
import BottomButtonsRegistration from "~/components/registration/BottomButtonsRegistration.vue";
import ContactRegistration from "~/components/registration/ContactRegistration.vue";
import InputsFirstRegistration from "~/components/registration/InputsFirstRegistration.vue";
import InputsSecondRegistration from "~/components/registration/InputsSecondRegistration.vue";
import InputsThirdRegistration from "~/components/registration/InputsThirdRegistration.vue";
import StepsInformation from "~/components/registration/StepsInformation.vue";
import TopInformationRegistration from "~/components/registration/TopInformationRegistration.vue";

const step = ref('1');

const changeStep = (): void => {
  if (step.value === "1") {
    step.value = "2";
    return;
  }
  if (step.value === "2") {
    step.value = "3";
    return;
  }
};
</script>

<template>
  <div class="registration-container">
    <form v-if="step" key="form" class="registration-modal">
      <transition-group
        name="shift"
        mode="out-in"
        tag="div"
        class="content-group"
      >
        <div :key="`top-info-${step}`" class="content-item">
          <TopInformationRegistration :step="step" />
        </div>
        <div key="steps" class="content-item">
          <StepsInformation :step="step" />
        </div>
        <div :key="`content-${step}`" class="content-item">
          <InputsFirstRegistration v-if="step === '1'" />
          <InputsSecondRegistration v-else-if="step === '2'" />
          <InputsThirdRegistration v-else-if="step === '3'" />
          <ContactRegistration v-if="step === '1'" />
        </div>
        <div key="bottom-buttons" class="content-item">
          <BottomButtonsRegistration @change-step="changeStep" :step="step" />
        </div>
      </transition-group>
    </form>
  </div>
</template>

<style lang="scss" scoped>
.registration-container {
  height: -webkit-fill-available;
}
.content-group {
  position: relative;
  transform-origin: top center;
}

.content-item {
  position: relative;
  width: 100%;
  transform-origin: top center;
  contain: layout style;
}

.shift {
  &-enter-active {
    transition: all 2s cubic-bezier(0.4, 0, 0.2, 1) 2s;
    overflow: hidden;
  }
  &-leave-active {
    transition: all 2s cubic-bezier(0.4, 0, 0.2, 1);
  }
  &-enter-from {
    opacity: 0;
    max-height: 0;
  }
  &-enter-to {
    opacity: 1;
    max-height: 1000px;
  }
  &-leave-from {
    opacity: 1;
    max-height: 500px;
  }
  &-leave-to {
    opacity: 0;
    max-height: 0;
  }
}

.registration-modal {
  transition: all 1s ease;
  margin-bottom: 24px;
  max-width: 542px;
  width: 100%;
  margin: 0 auto;
  background-color: #fff;
  border-radius: 24px;
  padding: 48px 24px;
  overflow: hidden;
  @media (max-width: 768px) {
    padding: 24px 16px 32px;
  }
}

.inputs {
  margin-bottom: 24px;
  .inputs-sharing {
    display: flex;
    gap: 16px;
  }
  .input-with-icons-container {
    position: relative;
    button {
      position: absolute;
      top: 14px;
      right: 16px;
    }
    input {
      padding: 12px 48px 12px 16px;
    }
  }
  display: flex;
  flex-direction: column;
  gap: 16px;
}
</style>
