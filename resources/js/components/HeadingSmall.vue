<script setup lang="ts">
const props = defineProps<{ title?: string; description?: string }>();
</script>

<template>
  <div class="mb-4">
    <h3 class="text-lg font-semibold text-fuchsia-700">{{ title }}</h3>
    <p v-if="description" class="text-sm text-gray-500 mt-1">{{ description }}</p>
  </div>
</template>
