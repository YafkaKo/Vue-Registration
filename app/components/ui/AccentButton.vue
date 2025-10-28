<script setup lang="ts">
const props = defineProps<{text:string}>()
</script>

<template>
  <button class="top-button">{{text}}</button>
</template>

<style lang="scss" scoped>
.top-button {
  font-family: "PP Neue Montreal Medium", sans-serif;
  font-size: 20px;
  line-height: 130%;
  width: 100%;
  background-color: #9747ff;
  border-radius: 12px;
  padding: 12px 0;
  color: #fff;
    @media(max-width: 768px){
    font-size: 16px;
      }
}
</style>
