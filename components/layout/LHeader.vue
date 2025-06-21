<script setup lang="ts">
const {t, locales, setLocale} = useI18n();
</script>

<template>
  <header class="flex items-center justify-right gap-8px max-md:justify-center h-55px b-b-(solid 1px gray-2) w-full px-24px max-md:sticky max-md:top-0 bg-white z-999">
    <LHeaderLink :text="t('layout.header.home')" icon="tabler:home" to="/" />
    <LHeaderLink :text="t('layout.header.what_is')" icon="tabler:sitemap" to="/about/" />
    <LHeaderDropdown :text="t('layout.header.change_lang')" icon="tabler:world">
      <div class="flex flex-col gap-5px">
        <button v-for="locale in locales" @click="setLocale(locale.code)" class="hover:bg-gray-1 transition-all duration-100 text-14px px-8px py-4px rounded-6px font-500 text-shadow-sm">
          {{ locale.name }}
        </button>
      </div>
    </LHeaderDropdown>
  </header>
</template>

<style scoped>

</style>