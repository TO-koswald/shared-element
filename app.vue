<template>
  <div class="bg-gray-50 h-screen">
    <div class="container mx-auto py-8">
      <NuxtPage />
    </div>
  </div>
</template>
<style>
.page-enter-active,
.page-leave-active {
  transition: all 0.4s;
}
.page-enter-from,
.page-leave-to {
  opacity: 0;
  filter: blur(1rem);
}
</style>