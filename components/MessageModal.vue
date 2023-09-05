<template>
  <generic-modal v-model="modelValueProxy">
    PRELOADED FROM THE SERVER: {{ data ?? 'LOADING...' }}
  </generic-modal>
</template>

<script setup>
import GenericModal from '~/components/GenericModal.vue';
console.log('MessageModal setup')

const props = defineProps({
  modelValue: { type: Boolean, required: true },
});

console.log('modelValue', props.modelValue)
const emit = defineEmits(['update:modelValue']);

const modelValueProxy = computed({
  get() {
    return props.modelValue;
  },

  set(value) {
    emit('update:modelValue', value);
  },
});

const data = ref(
  await new Promise((res) => {
    console.log('Start loading the data...');
    setTimeout(() => {
      console.log('THE DATA IS READY');
      res('DATA');
    }, 5000);
  })
);
</script>
