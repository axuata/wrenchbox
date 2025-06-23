<script setup lang="ts">
const props = defineProps<{
  title: string,
  desc: string,
  icon: string,
  to?: string
  target?: '_blank' | '_parent' | '_self' | '_top'
}>();
</script>

<template>
  <NuxtLinkLocale v-if="to" :to :target class="flex items-center gap-6px hover:scale-103 transition-all duration-100">
    <div class="bg-gray-1 size-50px rounded-12px flex items-center justify-center">
      <Icon :name="icon" class="size-25px" />
    </div>
    <div class="line-height-tight">
      <p class="text-20px font-600 text-gray-8 text-shadow-sm">{{ title }}</p>
      <p class="text-12px font-500 text-gray-6 mt-2px text-shadow-sm">{{ desc }}</p>
    </div>
  </NuxtLinkLocale>
  <div v-else class="flex items-center gap-6px hover:scale-103 transition-all duration-100">
    <div class="bg-gray-1 size-50px rounded-12px flex items-center justify-center">
      <Icon :name="icon" class="size-25px" />
    </div>
    <div class="line-height-tight">
      <p class="text-20px font-600 text-gray-8 text-shadow-sm">{{ title }}</p>
      <p class="text-12px font-500 text-gray-6 mt-2px text-shadow-sm">{{ desc }}</p>
    </div>
  </div>
</template>

<style scoped>

</style>