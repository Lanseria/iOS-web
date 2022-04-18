<script setup lang="ts">
import BScroll from '@better-scroll/core'
import Slide from '@better-scroll/slide'
import type { Ref } from 'vue'

BScroll.use(Slide)

const router = useRouter()
const slideRef = ref()

const slide: Ref<BScroll|undefined> = ref()

const activeIdx = ref(0)

const go = () => router.push('/apple_store')

onMounted(() => {
  slide.value = new BScroll(slideRef.value, {
    click: true,
    scrollX: true,
    scrollY: false,
    slide: {
      autoplay: false,
      loop: false,
    },
    momentum: false,
    bounce: false,
    probeType: 3,
  })
  // v2.1.0
  slide.value.on('slidePageChanged', (page: any) => {
    activeIdx.value = page.pageX
  })
})
</script>

<template>
  <div ref="slideRef" class="bg-img overflow-hidden relative h-full w-full bg-cover">
    <div class="relative h-full w-full">
      <div class="grid-icons-box">
        <div v-for="i in 24" :key="i" class="grid-app-item">
          <div
            class="icon-img grid-app-icon" @click="go"
          />
          <div class="text-xs mt-1">
            Apple Store
          </div>
        </div>
      </div>
      <div class="grid-icons-box">
        <div v-for="i in 24" :key="i" class="grid-app-item">
          <div
            class="icon-img grid-app-icon" @click="go"
          />
          <div class="text-xs mt-1">
            Apple Store
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="dot-wrapper absolute left-1/2 bottom-10">
    <div class="dot w-2 h-2 rounded" :class="{active: activeIdx===0}" />
    <div class="dot w-2 h-2 rounded" :class="{active: activeIdx===1}" />
  </div>
</template>

<style lang="css" scoped>
.bg-img {
  background-image: url('/cf3e07d9-56d5-4951-bd74-76ba57f0c717.jpg@s_2,w_820,h_1775');
}
.icon-img {
  background-image: url('/Apple Store-iOS-1024x1024.png');
}
.dot-wrapper {
  transform: translate(-50%, -50%);
  @apply flex;
}
.dot {
  @apply bg-gray-500 mx-1;
}
.active {
  @apply bg-gray-50;
}
</style>
