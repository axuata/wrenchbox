<script setup lang="ts">
const model = defineModel<any>();
const props = defineProps<{
  id?: string,
  name?: string,
  autoComplete?: string,
  variant?: 'border' | 'no-border' | 'ghost',
  leadingIcon?: string,
  trailingIcon?: string,
  length?: string,
  isRequired?: boolean,
  isAutoFocus?: boolean,
  isDisabled?: boolean
}>();

const classes = computed(() => {
  switch (props.variant) {
    case 'border':
      return 'b-(solid 1px gray-2) rounded-8px bg-white shadow-sm';
    case 'no-border':
      return 'rounded-8px bg-white';
    case 'ghost':
      return 'b-(solid 1px gray-1) rounded-8px bg-white shadow-md';
    default:
      return 'b-(solid 1px gray-2) rounded-8px bg-white shadow-sm';
  }
});
</script>

<template>
  <div :style="{ width: length }" :class="classes" class="px-6px py-4px flex items-center gap-6px">
    <Icon v-if="leadingIcon" :name="leadingIcon" class="text-gray-8" />
    <select v-model="model" :id :name :autocomplete="autoComplete" :required="isRequired" :autofocus="isAutoFocus" :disabled="isDisabled" class="focus:outline-none text-gray-7 font-500 w-full bg-white">
      <slot />
    </select>
    <Icon v-if="trailingIcon" :name="trailingIcon" class="text-gray-8" />
  </div>
</template>

<style scoped>

</style>