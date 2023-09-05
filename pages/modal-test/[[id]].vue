<template>
  <message-modal v-model="showModal" />

  <p>Click button to show modal.</p>
  <p>
    MessageModal is a sync component, so MessageModal.vue should be loaded from the server before you click.
    You can verify this in devtools.
  </p>
  <p>Modal should show animation.</p>

  <b-button @click="() => (showModal = true)">Show</b-button>
</template>

<script setup>
import MessageModal from '~/components/MessageModal.vue';

const showModal = ref(false);
console.log('The Modal is hidden...');
</script>
