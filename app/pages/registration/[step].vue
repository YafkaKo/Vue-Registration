<script setup lang="ts">
import { useRoute } from "vue-router";
import BottomButtonsRegistration from "~/components/registration/BottomButtonsRegistration.vue";
import ContactRegistration from "~/components/registration/ContactRegistration.vue";
import InputsFirstRegistration from "~/components/registration/InputsFirstRegistration.vue";
import InputsSecondRegistration from "~/components/registration/InputsSecondRegistration.vue";
import InputsThirdRegistration from "~/components/registration/InputsThirdRegistration.vue";
import TopInformationRegistration from "~/components/registration/TopInformationRegistration.vue";

const route = useRoute();
const step = route.params.step;

const suggestions = ["Москва", "Санкт-Петербург", "Новосибирск"];
</script>

<template>
  <form class="registration-modal">
    <TopInformationRegistration v-if="step" :step="step" />
    <InputsFirstRegistration v-if="step === '1'" />
    <InputsSecondRegistration v-if="step === '2'" />
    <InputsThirdRegistration v-if="step === '3'" />
    <ContactRegistration v-if="step === '1'" />
    <BottomButtonsRegistration v-if="step" :step="step" />
  </form>
</template>

<style lang="scss" scoped>
.registration-modal {
  margin-bottom: 24px;
  width: 542px;
  margin: 0 auto;
  background-color: #fff;
  border-radius: 24px;
  padding: 48px 24px;
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
