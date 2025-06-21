<script setup lang="ts">
const props = defineProps<{
  text: string,
  icon?: string
}>();
const isOpen = ref(false);
</script>

<template>
  <div class="relative">
    <div class="flex items-center gap-3px px-8px py-3px hover:bg-gray-1 rounded-8px transition-all duration-100 cursor-pointer" @click="isOpen = !isOpen">
      <Icon v-if="icon" :name="icon" class="text-gray-7 text-16px" />
      <span class="font-500 text-gray-7 text-shadow-sm text-14px">{{ text }}</span>
      <Icon v-if="isOpen" name="tabler:caret-up-filled" class="text-gray-7 text-15px" />
      <Icon v-if="!isOpen" name="tabler:caret-down-filled" class="text-gray-7 text-15px" />
    </div>
    <div v-if="isOpen" class="absolute flex w-full justify-center mt-3px">
      <div class="bg-white z-999 p-8px rounded-10px b-(solid 1px gray-2)">
        <slot />
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>