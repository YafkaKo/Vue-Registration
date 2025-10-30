<script setup lang="ts">
import { onClickOutside } from "@vueuse/core";
import { ref } from "vue";

const isOpenDataList = ref(false);
const inputValue = ref("");

const openDataList = () => {
  isOpenDataList.value = !isOpenDataList.value;
};

const selectSuggestion = (suggestion: string) => {
  inputValue.value = suggestion;
  isOpenDataList.value = false;
};

const containerRef = ref(null);
onClickOutside(containerRef, () => {
  isOpenDataList.value = false;
});

const props = defineProps<{
  suggestions: string[];
  name: string;
  id: string;
  placeholder: string;
}>();
</script>

<template>
  <div class="input-with-icons-container">
    <input
      class="input-with-icons"
      type="text"
      :name="name"
      :id="id"
      :placeholder="placeholder"
      v-model="inputValue"
      @focus="isOpenDataList = true"
    />
     <transition name="suggestions">
    <div v-if="isOpenDataList && suggestions.length" class="suggestions-list">
      <div
        v-for="suggestion in suggestions"
        :key="suggestion"
        class="suggestion-item"
        @click="selectSuggestion(suggestion)"
      >
        {{ suggestion }}
      </div>
    </div>
    </transition>
    <button @click.prevent="openDataList()">
      <img
        :class="!isOpenDataList ? 'btn-img-galochka' : 'btn-img-galochka btn-img-galochka-reverse'"
        src="@/assets/images/galochka.svg"
        alt=""
      />
    </button>
  </div>
</template>

<style lang="scss" scoped>

.suggestions-enter-active,
.suggestions-leave-active {
  transition: all 0.3s ease;
}

.suggestions-enter-from {
  opacity: 0;
}

.suggestions-leave-to {
  opacity: 0;
}
</style>
