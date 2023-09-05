<template>
  <b-modal v-model="show"><slot /></b-modal>
</template>

<script setup>
const props = defineProps({
  modelValue: { type: Boolean, required: true },
});

const emit = defineEmits(['update:modelValue']);

const show = ref(false)

watch(show, (newVal) => {
  emit('update:modelValue', newVal);
})

watch(() => props.modelValue, (newVal) => {
  show.value = newVal
})

// If the component has been instantiated with modelValue true, then there is an odd problem which means
// the modal animation doesn't work.  By using nextTick and a separate variable to control the modal
// show, we can make the modal animation work.
if (props.modelValue) {
  nextTick().then(() => {
    show.value = true
  })
}
</script>
