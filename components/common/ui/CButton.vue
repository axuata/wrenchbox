<script setup lang="ts">
const props = defineProps<{
  type: 'button' | 'link'
  text: string,
  icon?: string,
  to?: string,
  target?: '_blank' | '_parent' | '_self' | '_top'
}>();
</script>

<template>
  <button v-if="type === 'button'" class="b-(solid 1px gray-2) hover:b-gray-3 px-8px py-2px rounded-8px flex items-center gap-4px shadow-sm">
    <Icon v-if="icon" :name="icon" class="size-14px text-gray-7" />
    <span class="text-14px font-500 text-shadow-sm text-gray-8 select-none">{{ text }}</span>
  </button>
  <NuxtLinkLocale v-else-if="type === 'link'" :to :target class="b-(solid 1px gray-2) hover:b-gray-3 px-8px py-2px rounded-8px flex items-center gap-4px shadow-sm">
    <Icon v-if="icon" :name="icon" class="size-14px text-gray-7" />
    <span class="text-14px font-500 text-shadow-sm text-gray-8 select-none">{{ text }}</span>
  </NuxtLinkLocale>
</template>

<style scoped>

</style>