<script setup lang="ts">
import {v1 as uuidv1, v3 as uuidv3, v4 as uuidv4, v5 as uuidv5, v6 as uuidv6, v7 as uuidv7} from 'uuid';

const {t} = useI18n();
const uuidVersion = ref<'1' | '3' | '4' | '5' | '6' | '7'>('4');
const uuidCount = ref<number>(5);
const uuidName = ref<string>('');
const uuidNamespace = ref<string>('');
const generatedUuid = ref<string[]>([]);
const warning = computed(() => {
  if (uuidVersion.value === '3' || uuidVersion.value === '5') {
    if (uuidName.value === '' || uuidNamespace.value === '') {
      return t('tools.generators.uuid_generator.main.name_or_namespace_empty');
    } else {
      return '';
    }
  }
});

function generate() {
  let buffer = [];
  for (let i = 0; i < uuidCount.value; i++) {
    switch (uuidVersion.value) {
      case '1':
        buffer.push(uuidv1());
        break;
      case '3':
        buffer.push(uuidv3(uuidName.value, uuidNamespace.value));
        break;
      case '4':
        buffer.push(uuidv4());
        break;
      case '5':
        buffer.push(uuidv5(uuidName.value, uuidNamespace.value));
        break;
      case '6':
        buffer.push(uuidv6());
        break;
      case '7':
        buffer.push(uuidv7());
        break;
    }
  }

  console.log(buffer);
  generatedUuid.value = buffer;
}
</script>

<template>
  <div class="px-38px">
    <section class="py-58px line-height-tight">
      <h1 class="text-48px font-600 text-shadow-sm text-gray-8">{{ t('tools.generators.uuid_generator.meta.title') }}</h1>
      <p class="font-500 text-shadow-sm text-gray-6 text-15px mt-3px">{{ t('tools.generators.uuid_generator.meta.desc') }}</p>
    </section>
    <main class="flex flex-col bg-#fcfcfc p-20px b-(solid 1px gray-1) rounded-12px max-md:block gap-8px">
      <div>
        <h2 class="font-600 text-gray-7 text-18px text-shadow-sm">{{ t('tools.generators.uuid_generator.main.settings') }}</h2>
        <div class="flex gap-8px max-md:flex-col ">
          <div class="">
            <span class="text-14px font-500 text-gray-6 text-shadow-sm">{{ t('tools.generators.uuid_generator.main.uuid_version') }}</span>
            <div class="flex items-center gap-6px">
              <FSelect v-model="uuidVersion" length="150px">
                <option>1</option>
                <option>3</option>
                <option>4</option>
                <option>5</option>
                <option>6</option>
                <option>7</option>
              </FSelect>
            </div>
          </div>
          <div>
            <span class="text-14px font-500 text-gray-6 text-shadow-sm">{{ t('tools.generators.uuid_generator.main.uuid_count') }}</span>
            <div class="flex items-center gap-6px">
              <FNumber v-model="uuidCount" type="input"/>
            </div>
          </div>
          <div>
            <span class="text-14px font-500 text-gray-6 text-shadow-sm">{{ t('tools.generators.uuid_generator.main.advanced_settings') }}</span>
            <div class="flex items-center gap-6px">
              <FText v-model="uuidName" :placeholder="t('tools.generators.uuid_generator.main.name')" length="150px"/>
              <FText v-model="uuidNamespace" :placeholder="t('tools.generators.uuid_generator.main.namespace')" length="400px"/>
            </div>
          </div>
        </div>
      </div>
      <div class="max-md:py-8px">
        <CButton type="button" :text="t('tools.generators.uuid_generator.main.generate')" icon="tabler:rotate" @click="generate"/>
      </div>
      <div v-if="warning" class="b-(solid 1px orange-2) bg-orange-1 px-8px py-3px rounded-8px text-14px font-500 text-gray-7">
        <p>{{ warning }}</p>
      </div>
      <div class="flex flex-col bg-white p-8px rounded-10px b-(solid 1px gray-2) gap-8px">
        <p v-if="generatedUuid.length === 0" class="text-shadow-sm font-500 text-gray-6 oblique text-14px">{{ t('tools.generators.uuid_generator.main.nothing') }}</p>
        <p v-else v-for="uuid in generatedUuid" class="text-shadow-sm font-500 text-gray-8">{{ uuid }}</p>
      </div>
    </main>
  </div>
</template>

<style scoped>

</style>