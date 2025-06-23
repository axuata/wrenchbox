<script setup lang="ts">
const {t} = useI18n();
</script>

<template>
  <aside class="w-300px h-100vh flex flex-col max-md:h-auto max-md:w-100vw b-r-(solid 1px gray-2) max-md:b-r-none max-md:b-b-(solid 1px gray-2)">
    <section class="flex flex-col py-32px text-center">
      <div class="flex items-center justify-center gap-6px">
        <NuxtImg src="/favicon.svg" class="size-22px" />
        <span class="text-22px font-700 text-shadow-sm text-gray-8">{{ t('layout.sidebar.hero.title') }} 🚧</span>
      </div>
    </section>

    <section class="px-16px flex flex-col gap-7px">
      <LSidebarLink :text="t('layout.sidebar.pages.home')" icon="tabler:home" to="/" />
      <LSidebarLink :text="t('layout.sidebar.pages.changelog')" icon="tabler:sitemap" to="/changelog/" />
    </section>

    <div class="w-full h-1px bg-gray-2 my-10px" />

    <section class="flex flex-col gap-18px">
      <LSidebarToolGroup :title="t('layout.sidebar.tools.text')" tag="text">
        <NuxtLinkLocale to="/tools/text/character-counter/" class="flex items-center gap-3px text-14px py-4px px-8px font-500 text-shadow-sm bg-#f9f9f9 text-gray-8 hover:bg-gray-1 transition-all duration-100 w-full rounded-8px">
          <Icon name="tabler:abc" class="text-16px" />
          <span>{{ t('tools.text.character_counter.meta.title') }}</span>
        </NuxtLinkLocale>
      </LSidebarToolGroup>
      <LSidebarToolGroup :title="t('layout.sidebar.tools.generators')" tag="generators">
        <NuxtLinkLocale to="/tools/generators/uuid-generator/" class="flex items-center gap-3px text-14px py-4px px-8px font-500 text-shadow-sm bg-#f9f9f9 text-gray-8 hover:bg-gray-1 transition-all duration-100 w-full rounded-8px">
          <Icon name="tabler:abc" class="text-16px" />
          <span>{{ t('tools.generators.uuid_generator.meta.title') }}</span>
        </NuxtLinkLocale>
      </LSidebarToolGroup>
    </section>

    <footer class="mt-auto flex flex-col text-center py-24px">
      <p class="text-14px font-600 text-shadow-sm text-gray-7">© 2025 Axuata.</p>
      <p class="text-14px font-600 text-shadow-sm text-gray-7">Licensed under the <a href="https://opensource.org/licenses/MIT">MIT License</a>.</p>
      <p class="text-14px font-600 text-shadow-sm text-gray-7">Icons by <a href="https://tabler.io/icons">Tabler</a> and <a href="https://github.com/microsoft/fluentui-emoji">Fluent Emoji</a>.</p>
    </footer>
  </aside>
</template>

<style scoped>

</style>