<script setup lang="ts">
import { onMounted, onUnmounted, ref } from "vue";
import { useRoute } from "vue-router";
import AddContactModal from "~/components/contact/AddContactModal.vue";
const route = useRoute();
const title = ref("");

if (route.path === "/contact/vk") {
  title.value = "ВКонтакте";
} else {
  title.value = "Telegram";
}

onMounted(() => {
  document.body.classList.add("special-page-active");
});

onUnmounted(() => {
  document.body.classList.remove("special-page-active");
});
</script>

<template>
  <AddContactModal :title="title" />
</template>

<style>
body.special-page-active {
  background-image: none;
}
</style>
