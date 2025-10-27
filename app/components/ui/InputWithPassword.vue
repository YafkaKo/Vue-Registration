<script setup lang="ts">
import { ref } from "vue";

const inputValue = ref("");
const isShowPassword = ref(false)


  const setShowPassword = () =>{
      isShowPassword.value=!isShowPassword.value
  }

const props = defineProps<{
  name: string;
  id: string;
  placeholder: string;
}>();
</script>

<template>
          <div class="input-with-icons-container">
          <input  :type="isShowPassword ? 'text' : 'password'" :name="name" :id="id" :placeholder="placeholder" v-model="inputValue" autocomplete="new-password"></input>
          <button v-if="!isShowPassword" @click.prevent="setShowPassword()"><img src="@/assets/images/Vector.svg" alt=""></button>
          <button v-else @click.prevent="setShowPassword()"><img src="@/assets/images/Union.svg" alt=""></button>
          </div>
</template>
