<script setup lang="ts">
// DaisyUI error message component
const props = defineProps<{ message?: string }>();
</script>

<template>
  <div v-if="message" class="text-error text-sm mt-1">
    {{ message }}
  </div>
</template>
