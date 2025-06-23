<script setup lang="ts">
const {t} = useI18n();

type Update = {
  date: string,
  title: string,
  desc: string
}

const updates: Update[] = [
  {
    date: '2025-06-22',
    title: t('pages.changelog.items.added_updates_page.title'),
    desc: t('pages.changelog.items.added_updates_page.desc')
  },
  {
    date: '2025-06-21',
    title: t('pages.changelog.items.added_uuid_tool.title'),
    desc: t('pages.changelog.items.added_uuid_tool.desc')
  },
  {
    date: '2025-06-21',
    title: t('pages.changelog.items.alpha_published.title'),
    desc: t('pages.changelog.items.alpha_published.desc')
  }
];
</script>

<template>
  <main class="px-38px">
    <section class="py-58px line-height-tight">
      <p class="text-50px font-600 text-shadow-md text-gray-8">{{ t('pages.changelog.title.title') }}</p>
      <p class="text-gray-6 font-500 text-shadow-sm">{{ t('pages.changelog.title.desc') }}</p>
    </section>

    <section class="flex flex-col gap-28px">
      <div v-for="update in updates" class="flex gap-12px">
        <div>
          <p class="text-18px font-600 text-shadow-sm text-gray-7 mt-3px">{{ update.date }}</p>
        </div>
        <div>
          <p class="text-22px font-600 text-shadow-sm text-gray-8">{{ update.title }}</p>
          <p class="text-14px font-500 text-shadow-sm text-gray-7">{{ update.desc }}</p>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>

</style>