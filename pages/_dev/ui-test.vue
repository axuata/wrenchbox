<script setup lang="ts">
import FTextarea from "~/components/common/form/FTextarea.vue";

const values = ref({
  text: 'Initial Value',
  number: 12,
  textarea: 'Initial Textarea Value'
});
</script>

<template>
  <div class="m-20px text-18px font-500 text-gray-8">
    <p>text: {{ values.text }}</p>
    <p>number: {{ values.number }}</p>
    <p>textarea: {{ values.textarea }}</p>
  </div>
  <main class="m-20px flex flex-col gap-8px">
    <section class="bg-white b-(solid 1px gray-2) rounded-12px p-16px flex flex-col gap-8px">
      <FText v-model="values.text" />
      <FText v-model="values.text" length="100px" />
      <FText v-model="values.text" length="200px" />
      <FText v-model="values.text" length="400px" />
      <FText v-model="values.text" :max-length="20" />
    </section>
    <section class="bg-white b-(solid 1px gray-2) rounded-12px p-16px flex flex-col gap-8px">
      <FText v-model="values.text" leading-icon="tabler:icons" />
      <FText v-model="values.text" leading-icon="tabler:icons" trailing-icon="tabler:icons" />
      <FText v-model="values.text" trailing-icon="tabler:icons" />
    </section>
    <section class="bg-white b-(solid 1px gray-2) rounded-12px p-16px flex flex-col gap-8px">
      <FText v-model="values.text" variant="border" length="250px" />
      <FText v-model="values.text" variant="no-border" length="250px" />
      <FText v-model="values.text" variant="ghost" length="250px" />
    </section>
    <section class="bg-white b-(solid 1px gray-2) rounded-12px p-16px flex flex-col gap-8px">
      <FNumber v-model="values.number" type="input" />
      <FNumber v-model="values.number" type="input" leading-icon="tabler:icons" />
      <FNumber v-model="values.number" type="input" trailing-icon="tabler:icons" />
      <FNumber v-model="values.number" type="updown" />
      <FNumber v-model="values.number" type="updown" :min="3" :max="20" />
      <FNumber v-model="values.number" type="updown" :min="3" :max="20" :step="3" />
    </section>
    <section class="bg-white b-(solid 1px gray-2) rounded-12px p-16px flex flex-col gap-8px">
      <FTextarea v-model="values.textarea" />
      <FTextarea v-model="values.textarea" width="200px" height="200px" />
      <FTextarea v-model="values.textarea" width="250px" height="400px" is-resizable />
      <FTextarea v-model="values.textarea" :max-length="18" />
    </section>
  </main>
</template>

<style scoped>

</style>