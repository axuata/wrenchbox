<script setup lang="ts">

</script>

<template>
  <div class="max-md:hidden flex">
    <div class="flex-shrink-0">
      <LSidebar />
    </div>
    <div class="w-full">
      <LHeader />
      <div class="overflow-y-scroll h-[calc(100vh-55px)]">
        <slot />
      </div>
    </div>
  </div>
  <div class="hidden max-md:block">
    <LHeader />
    <LSidebar />
    <div class="w-full">
      <slot />
    </div>
  </div>
</template>

<style scoped>

</style>