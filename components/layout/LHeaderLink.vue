<script setup lang="ts">
const props = defineProps<{
  text: string,
  icon?: string,
  to?: string,
  target?: '_blank' | '_parent' | '_self' | '_top'
}>();
</script>

<template>
  <NuxtLinkLocale :to :target class="flex items-center gap-3px px-8px py-3px hover:bg-gray-1 rounded-8px transition-all duration-100">
    <Icon v-if="icon" :name="icon" class="text-gray-7 text-16px" />
    <span class="font-500 text-gray-7 text-shadow-sm text-14px">{{ text }}</span>
  </NuxtLinkLocale>
</template>

<style scoped>

</style>