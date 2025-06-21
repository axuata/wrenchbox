<script setup lang="ts">
const props = defineProps<{
  title: string,
  tag: string
}>();
</script>

<template>
  <div class="px-16px">
    <div class="flex justify-between items-center">
      <p class="text-14px font-500 text-gray-8 text-shadow-sm">{{ title }}</p>
      <p class="text-13px font-600 text-gray-6 b-(solid 1px gray-2) py-1px px-6px rounded-6px shadow-sm cursor-default select-none">{{ tag }}</p>
    </div>
    <div class="flex flex-col gap-3px mt-4px w-full">
      <slot />
    </div>
  </div>
</template>

<style scoped>

</style>