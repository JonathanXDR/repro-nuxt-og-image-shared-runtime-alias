<script setup lang="ts">
// This import is the exact line the `npx nuxt-og-image create` CLI emits
// (see node_modules/nuxt-og-image/dist/cli.mjs:57) and the line that breaks:
//   - typecheck: TS2307 "Cannot find module '#og-image/app/utils'"
//   - nuxi build: vite:load-fallback ENOENT on dist/shared/runtime/app/utils
import { useOgImageRuntimeConfig } from '#og-image/app/utils'

const runtimeConfig = useOgImageRuntimeConfig()

withDefaults(
  defineProps<{
    title?: string
    description?: string
  }>(),
  { title: 'title', description: 'description' },
)

void runtimeConfig
</script>

<template>
  <div class="w-full h-full flex items-center justify-center bg-white text-gray-900">
    <div>
      <h1 class="text-6xl font-bold">{{ title }}</h1>
      <p class="text-2xl mt-4">{{ description }}</p>
    </div>
  </div>
</template>
