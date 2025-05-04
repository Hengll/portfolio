<template>
  <div
    class="loading-page absolute w-full h-dvh bg-gray-300 flex flex-col justify-center items-center"
  >
    <DotLottieVue
      style="height: 200px; width: 200px"
      autoplay
      loop
      src="/Animation-1743077041364.lottie"
    />
    <p class="name text-5xl mt-5">Heng Li</p>
  </div>
  <div v-if="!isLoading" class="contect-page">
    <div class="first-view container mx-auto px-10 h-dvh bg-amber-300"></div>
    <div class="about container mx-auto px-10 h-dvh bg-amber-500"></div>
    <div class="portfolio container mx-auto px-10 h-dvh bg-amber-700"></div>
    <div class="contact container mx-auto px-10 h-dvh bg-amber-900"></div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { DotLottieVue } from '@lottiefiles/dotlottie-vue' // 沙漏動畫套件

let isLoading = ref(true)

setTimeout(() => {
  isLoading.value = false
}, 4000)
</script>
