<script setup lang="ts">
const props = defineProps<{ title?: string; description?: string }>();
</script>

<template>
  <div class="mb-6">
    <h2 class="text-2xl font-bold text-fuchsia-700">{{ title }}</h2>
    <p v-if="description" class="text-sm text-gray-500 mt-1">{{ description }}</p>
  </div>
</template>
