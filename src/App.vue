<script setup lang="ts">
import { H1 as iH1 } from '@ios-web/components'
</script>
<template>
  <iH1 />
  <main font-sans font-medium p="x-0 y-0 sm:x-4 sm:y-10" h="full" text="center gray-700 dark:gray-200">
    <div class="w-full sm:w-97.5 h-full sm:h-221 m-auto bg-white sm:rounded-3xl relative">
      <router-view />
    </div>
  </main>
</template>
