<script setup lang="ts">
const model = defineModel<number>();
const props = defineProps<{
  type?: 'updown' | 'input',
  min?: number,
  max?: number,
  step?: number,
  id?: string,
  name?: string,
  placeholder?: string,
  variant?: 'border' | 'no-border' | 'ghost',
  autoComplete?: string,
  leadingIcon?: string,
  trailingIcon?: string,
  length?: string,
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

function onClick(type: 'decrease' | 'increase') {
  if (model.value != null) {
    if (type === 'decrease') {
      if (props.min && model.value <= props.min) {
        return;
      } else {
        if (props.step) {
          if (props.min && model.value - props.step < props.min) {
            return;
          } else {
            model.value = model.value - props.step;
          }
        } else {
          model.value --;
        }
      }
    } else if (type === 'increase') {
      if (props.max && model.value >= props.max) {
        return;
      } else {
        if (props.step) {
          if (props.max && model.value + props.step > props.max) {
            return;
          } else {
            model.value = model.value + props.step;
          }
        } else {
          model.value ++;
        }
      }
    }
  }
}
</script>

<template>
  <div v-if="type === 'updown'" class="flex items-center">
    <button class="b-(solid 1px gray-2) flex items-center justify-center p-3px rounded-6px hover:b-gray-3 bg-white" @click="onClick('decrease')"><Icon name="tabler:caret-left-filled" /></button>
    <span class="w-40px text-center">{{ model }}</span>
    <button class="b-(solid 1px gray-2) flex items-center justify-center p-3px rounded-6px hover:b-gray-3 bg-white" @click="onClick('increase')"><Icon name="tabler:caret-right-filled" /></button>
  </div>
  <div v-else :style="{ width: length }" :class="classes" class="px-6px py-2px flex items-center gap-6px">
    <Icon v-if="leadingIcon" :name="leadingIcon" class="text-gray-8" />
    <input v-model="model" :id :name type="number" :placeholder :autocomplete="autoComplete" :required="isRequired" :autofocus="isAutoFocus" :disabled="isDisabled" :readonly="isReadOnly" class="focus:outline-none text-gray-7 font-500 w-full">
    <Icon v-if="trailingIcon" :name="trailingIcon" class="text-gray-8" />
  </div>
</template>

<style scoped>

</style>