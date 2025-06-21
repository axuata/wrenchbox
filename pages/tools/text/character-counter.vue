<script setup lang="ts">
const {t} = useI18n();
const text = ref('');
const results = computed(() => {
  const userLines = text.value.split('\n');

  let lines = 0;
  let linesWithoutEmptyLines = 0;

  userLines.forEach(line => {
    if (line === '') {
      lines ++;
    } else {
      lines ++;
      linesWithoutEmptyLines ++;
    }
  });

  return [
    {
      id: 'length',
      name: t('tools.text.character_counter.main.results.length'),
      value: text.value.length
    },
    {
      id: 'lengthWithoutSpaceAndBreaks',
      name: t('tools.text.character_counter.main.results.lengthWithoutSpaceAndBreaks'),
      value: text.value.replace(/\s/g, '').length
    },
    {
      id: 'lengthWithoutBreaks',
      name: t('tools.text.character_counter.main.results.lengthWithoutBreaks'),
      value: text.value.replace(/\r\n/g, '').length
    },
    {
      id: 'lines',
      name: t('tools.text.character_counter.main.results.lines'),
      value: lines ? lines : 0
    },
    {
      id: 'linesWithoutEmptyLines',
      name: t('tools.text.character_counter.main.results.linesWithoutEmptyLines'),
      value: linesWithoutEmptyLines ? linesWithoutEmptyLines : 0
    }
  ];
});

const dataMode = ref<'json' | 'yaml'>('json');
const generatedData = computed(() => {
  let jsonData = [];
  let yamlData = [];

  jsonData.push('{');
  yamlData.push('results:')
  results.value.forEach((result) => {
    jsonData.push(`  "${result.id}": ${result.value}`);
    yamlData.push(`  ${result.id}: ${result.value}`);
  });
  jsonData.push('}');

  return {
    jsonData: jsonData.join('\n'),
    yamlData: yamlData.join('\n')
  };
});

function onCopyData() {
  if (dataMode.value === 'json') {
    navigator.clipboard.writeText(generatedData.value.jsonData);
  } else if (dataMode.value === 'yaml') {
    navigator.clipboard.writeText(generatedData.value.yamlData);
  }
}
</script>

<template>
  <div class="px-38px">
    <section class="py-58px line-height-tight">
      <h1 class="text-48px font-600 text-shadow-sm text-gray-8">{{ t('tools.text.character_counter.meta.title') }}</h1>
      <p class="font-500 text-shadow-sm text-gray-6 text-15px mt-3px">{{ t('tools.text.character_counter.meta.desc') }}</p>
    </section>
    <main class="flex bg-#fcfcfc p-20px b-(solid 1px gray-1) rounded-12px max-md:block gap-10px">
      <section class="w-300px max-md:w-full flex-shrink-0">
        <div class="bg-white px-12px py-14px b-(solid 1px gray-2) rounded-12px shadow-sm font-500 text-shadow-sm flex flex-col gap-10px">
          <div v-for="result in results" class="flex justify-between items-center">
            <span class="text-gray-7">{{ result.name }}</span>
            <span class="font-600">{{ result.value }}</span>
          </div>
        </div>
        <div class="bg-white b-(solid 1px gray-2) rounded-12px shadow-sm flex flex-col gap-10px mt-10px">
          <div class="bg-gray-1 rounded-t-12px p-6px flex justify-between font-500 text-shadow-sm">
            <div class="flex gap-4px">
              <button class="text-14px bg-white py-2px px-6px rounded-8px b-(solid 1px gray-2) shadow-sm text-shadow-sm hover:b-gray-3" @click="dataMode = 'json'">JSON</button>
              <button class="text-14px bg-white py-2px px-6px rounded-8px b-(solid 1px gray-2) shadow-sm text-shadow-sm hover:b-gray-3" @click="dataMode = 'yaml'">YAML</button>
            </div>
            <div>
              <button class="flex items-center gap-3px text-14px bg-white py-2px px-6px rounded-8px b-(solid 1px gray-2) shadow-sm text-shadow-sm hover:b-gray-3" @click="onCopyData()">
                <Icon name="tabler:copy" />
                <span>{{ t('tools.text.character_counter.main.copy') }}</span>
              </button>
            </div>
          </div>
          <div class="font-mono text-14px whitespace-pre px-10px pb-10px">
            <template v-if="dataMode === 'json'">
              {{ generatedData.jsonData }}
            </template>
            <template v-else-if="dataMode === 'yaml'">
              {{ generatedData.yamlData }}
            </template>
          </div>
        </div>
      </section>
      <section class="w-full max-md:mt-8px">
        <FTextarea v-model="text" width="100%" height="100%" :placeholder="t('tools.text.character_counter.main.enter_here')" />
      </section>
    </main>
  </div>
</template>

<style scoped>

</style>