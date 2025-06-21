<script setup lang="ts">
const model = defineModel<string>();
const props = defineProps<{
  id?: string,
  name?: string,
  placeholder?: string,
  variant?: 'border' | 'no-border' | 'ghost',
  width?: string,
  height?: string,
  maxLength?: number,
  isRequired?: boolean,
  isAutoFocus?: boolean,
  isDisabled?: boolean,
  isReadOnly?: boolean,
  isResizable?: boolean
}>();

const classes = computed(() => {
  let classes = [];

  if (!props.isResizable) {
    classes.push('resize-none');
  }

  switch (props.variant) {
    case 'border':
      classes.push('b-(solid 1px gray-2) rounded-8px bg-white shadow-sm');
      break;
    case 'no-border':
      classes.push('rounded-8px bg-white');
      break
    case 'ghost':
      classes.push('b-(solid 1px gray-1) rounded-8px bg-white shadow-md');
      break;
    default:
      classes.push('b-(solid 1px gray-2) rounded-8px bg-white shadow-sm');
      break;
  }

  return classes.join(' ');
});
</script>

<template>
  <textarea v-model="model" :id :name :placeholder :maxlength="maxLength" :class="classes" :style="{ width: width, height: height }" :required="isRequired" :autofocus="isAutoFocus" :disabled="isDisabled" :readonly="isReadOnly" class="px-8px py-6px focus:outline-none text-gray-7 font-500"></textarea>
</template>

<style scoped>

</style>