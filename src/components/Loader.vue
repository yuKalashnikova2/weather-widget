<template>
  <div class="loader"></div>
</template>

<style lang="scss" scoped>
.loader {
  width: 150px;
  height: 150px;
  border: 30px solid rgba(167, 196, 156, 0.5);
  border-radius: 50%;
  border-left-color: rgb(155, 162, 143);
  transition: 3s;
  animation: loader 1.5s linear infinite;

  @keyframes loader {
    100% {
      rotate: 360deg;
    }
  }
}
</style>
