<script setup lang="ts">
const model = defineModel<string>();
const props = defineProps<{
  id?: string,
  name?: string,
  type?: string,
  placeholder?: string,
  variant?: 'border' | 'no-border' | 'ghost',
  autoComplete?: string,
  leadingIcon?: string,
  trailingIcon?: string,
  length?: string,
  maxLength?: number,
  isRequired?: boolean,
  isAutoFocus?: boolean,
  isDisabled?: boolean,
  isReadOnly?: boolean
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
  <div :style="{ width: length }" :class="classes" class="px-6px py-2px flex items-center gap-6px">
    <Icon v-if="leadingIcon" :name="leadingIcon" class="text-gray-8" />
    <input v-model="model" :id :name :type="type || 'text'" :placeholder :maxlength="maxLength" :autocomplete="autoComplete" :required="isRequired" :autofocus="isAutoFocus" :disabled="isDisabled" :readonly="isReadOnly" class="focus:outline-none text-gray-7 font-500 w-full">
    <Icon v-if="trailingIcon" :name="trailingIcon" class="text-gray-8" />
  </div>
</template>

<style scoped>

</style>