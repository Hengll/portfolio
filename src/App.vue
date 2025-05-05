<template>
  <div class="loading-page absolute w-full h-dvh flex flex-col justify-center items-center">
    <DotLottieVue
      style="height: 200px; width: 200px"
      autoplay
      loop
      src="/Animation-1743077041364.lottie"
    />
    <p class="name select-none text-5xl mt-15">Heng Li</p>
  </div>
  <div v-if="!isLoading" class="contect-page">
    <FirstView class="first-view container mx-auto px-10 h-dvh bg-amber-300" />
    <AboutMe class="about-me container mx-auto px-10 h-dvh bg-amber-500" />
    <MyPortfolio class="my-portfolio container mx-auto px-10 h-dvh bg-amber-700" />
    <ContactMe class="contact-me container mx-auto px-10 h-dvh bg-amber-900" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { DotLottieVue } from '@lottiefiles/dotlottie-vue' // 沙漏動畫套件
import { gsap } from 'gsap'
import { SplitText } from 'gsap/SplitText'

import FirstView from './components/FirstView.vue'
import AboutMe from './components/AboutMe.vue'
import MyPortfolio from './components/MyPortfolio.vue'
import ContactMe from './components/ContactMe.vue'

gsap.registerPlugin(SplitText)

let isLoading = ref(true)
let splitName
let timeLine

onMounted(() => {
  splitName = SplitText.create('.name', { type: 'words, chars' })

  timeLine = gsap.timeline()
  timeLine.fromTo(
    splitName.chars,
    { y: 20 },
    {
      y: -20,
      duration: 0.38,
      ease: 'sine.inOut',
      stagger: {
        each: 0.1,
        repeat: 1,
        yoyo: true,
      },
      repeat: 2,
      delay: 0.1,
      onComplete: () => {
        isLoading.value = false

        // gsap.to('.loading-page', {
        //   alpha: 0,
        //   direction: 1,
        // })
      },
    },
  )
})
</script>
