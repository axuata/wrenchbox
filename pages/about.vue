<script setup lang="ts">
const {t} = useI18n();
</script>

<template>
  <div class="px-38px">
    <section class="py-64px line-height-tight">
      <p class="text-48px font-700 text-shadow-sm text-gray-8">{{ t('pages.about.title') }}</p>
    </section>

    <main class="typography flex flex-col gap-40px">
      <div>
        <h1>{{ t('pages.about.main.what_is.headline') }}</h1>
        <p>{{ t('pages.about.main.what_is.is_a') }}</p>
        <p>{{ t('pages.about.main.what_is.add') }}</p>
      </div>
      <div>
        <h1>{{ t('pages.about.main.using.headline') }}</h1>
        <ul>
          <li><a href="https://nuxt.com/">Nuxt</a> - {{ t('pages.about.main.using.nuxt') }}</li>
          <li><a href="https://vuejs.org/">Vue.js</a> - {{ t('pages.about.main.using.vuejs') }}</li>
          <li><a href="https://unocss.dev/">UnoCSS</a> - {{ t('pages.about.main.using.unocss') }}</li>
        </ul>
      </div>
    </main>
  </div>
</template>

<style scoped>
.typography {
  p {
    @apply text-15px font-500 text-shadow-sm text-gray-7;
  }

  ul {
    @apply my-2px;

    li {
      @apply text-gray-7 font-500 list-disc-inside text-shadow-sm;
    }
  }

  h1 {
    @apply text-32px font-700 text-gray-8 text-shadow-sm;
  }
}
</style>