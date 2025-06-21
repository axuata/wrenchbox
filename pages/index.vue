<script setup lang="ts">
const {t, localeProperties} = useI18n();

type Update = {
  date: string,
  title: string,
  desc: string
}

const updates: Update[] = [
  {
    date: '2025-06-21',
    title: t('pages.home.updates.0.title'),
    desc: t('pages.home.updates.0.desc'),
  }
];
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
        <CButton type="link" :text="t('pages.home.links.what_is')" icon="tabler:sitemap" to="/about/" />
      </div>
      <div class="flex flex-wrap gap-24px">
        <CIconCard :title="t('pages.home.features.lightweight.title')" :desc="t('pages.home.features.lightweight.desc')" icon="twemoji:high-voltage" />
        <CIconCard :title="t('pages.home.features.secure.title')" :desc="t('pages.home.features.secure.desc')" icon="twemoji:shield" />
      </div>
    </section>

    <section>
      <div>
        <p class="text-24px font-600 text-shadow-sm text-gray-8">{{ t('pages.home.updates.title') }}</p>
      </div>
      <div class="py-12px flex flex-col gap-8px">
        <div v-for="update in updates" class="flex gap-12px">
          <div class="pt-3px">
            <p class="font-500 text-shadow-sm text-gray-7">{{ update.date }}</p>
          </div>
          <div>
            <p class="text-shadow-sm text-gray-8 font-700 text-20px">{{ update.title }}</p>
            <p class="text-shadow-sm text-gray-7 font-500 text-14px">{{ update.desc }}</p>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.developer-shadow {
  text-shadow: 0 0 24px #8dccfd;
}
</style>