<template>
  <message-modal v-if="showModal" v-model="showModal" />

  <p>Click button to show modal.</p>
  <p>
    MessageModal is an async component, so MessageModal.vue should not be loaded from the server until you click.
    You can verify this in devtools.
  </p>
  <p>Modal should show animation.</p>

  <b-button @click="() => (showModal = true)">Show</b-button>
</template>

<script setup>
const MessageModal = defineAsyncComponent(() =>
  import('~/components/MessageModal.vue')
);

const showModal = ref(false);
</script>
