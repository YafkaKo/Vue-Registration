<script setup lang="ts">
const props = defineProps<{
  name: string;
  id: string;
  placeholder: string;
  label: string;
}>();
</script>

<template>
  <div class="input-with-icons-container">
    <input
      type="file"
      :name="name"
      :id="id"
      :placeholder="placeholder"
      accept=".jpg, .jpeg, .png"
    />
    <label class="label-file" for="StudyBook">{{ placeholder }}
      <span ><img src="@/assets/images/screpka.svg" alt=""></span>
    </label>
      <p>{{ label }}</p>
  </div>
</template>

<style lang="scss" scoped>
.input-with-icons-container{
    input{
      opacity: 0;
      visibility: hidden;
      position: absolute;
      z-index: 2;
      position: absolute;
    }
    .label-file {
      display: block;
      border: 1px solid $teriary-dark;
      border-radius: 12px;
      padding: 12px 16px;
      font-family: "PP Neue Montreal Medium", sans-serif;
      line-height: 130%;
      font-size: 16px;
      color: $teriary-dark;
      &::placeholder {
        opacity: 50%;
      }
}
span{
  cursor: pointer;
    position: absolute;
    top: 11px;
    right: 16px;
}
p{
  font-family: 'PP Neue Montreal Medium';
  font-size: 12px;
  line-height: 14px;
  color: $teriary-dark;
  padding: 4px 16px 0px 16px;
}
}
</style>
