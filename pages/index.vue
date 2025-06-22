<script setup lang="ts">
const {t, localeProperties} = useI18n();
</script>

<template>
  <main class="px-38px">
    <section class="py-72px flex flex-col gap-16px">
      <div class="text-48px font-700 line-height-tight">
        <p class="text-shadow-md text-gray-8">Wrenchbox 🔧</p>
        <p v-if="localeProperties.code === 'ja'"><span class="developer-shadow text-blue-5">{{ t('pages.home.hero.developers') }}</span><span class="text-shadow-md text-gray-8">{{ t('pages.home.hero.toolbox') }}</span></p>
        <p v-else><span class="text-shadow-md text-gray-8">{{ t('pages.home.hero.toolbox') }}</span> <span class="developer-shadow text-blue-5">{{ t('pages.home.hero.developers') }}</span></p>
      </div>
      <div class="flex gap-5px">
        <CButton type="link" text="GitHub" icon="logos:github-icon" to="https://github.com/axuata/wrenchbox" />
      </div>
      <div class="flex flex-wrap gap-24px">
        <CIconCard :title="t('pages.home.features.lightweight.title')" :desc="t('pages.home.features.lightweight.desc')" icon="twemoji:high-voltage" />
        <CIconCard :title="t('pages.home.features.secure.title')" :desc="t('pages.home.features.secure.desc')" icon="twemoji:shield" />
      </div>
    </section>

    <section class="typography flex flex-col gap-48px">
      <div>
        <h1>{{ t('pages.home.about.main.what_is.headline') }}</h1>
        <p>{{ t('pages.home.about.main.what_is.is_a') }}</p>
        <p>{{ t('pages.home.about.main.what_is.add') }}</p>
      </div>
      <div>
        <h1>{{ t('pages.home.about.main.using.headline') }}</h1>
        <ul>
          <li><a href="https://nuxt.com/">Nuxt</a> - {{ t('pages.home.about.main.using.nuxt') }}</li>
          <li><a href="https://vuejs.org/">Vue.js</a> - {{ t('pages.home.about.main.using.vuejs') }}</li>
          <li><a href="https://unocss.dev/">UnoCSS</a> - {{ t('pages.home.about.main.using.unocss') }}</li>
        </ul>
      </div>
    </section>
  </main>
</template>

<style scoped>
.developer-shadow {
  text-shadow: 0 0 24px #8dccfd;
}

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