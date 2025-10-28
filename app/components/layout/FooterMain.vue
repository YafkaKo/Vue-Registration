<template>
  <footer>
    <p class="politicy">Политика конфиденциальности</p>
    <p class="info">Проект запущен: 2024 © Study</p>
  </footer>
</template>

<style lang="scss" scoped>
footer {
  font-family: "PP Neue Montreal Medium";
  font-weight: 500;
  font-size: 16px;
  color: #fff;
  padding: 20px 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  text-align: center;
}
@media(max-width: 768px){
  footer{
  flex-direction: column;
  gap: 8px;
  }
}
</style>
