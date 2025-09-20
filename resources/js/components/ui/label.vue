<script setup lang="ts">
const props = defineProps<{ for?: string; class?: string }>();
</script>
<template>
  <label :for="props.for" :class="['label', props.class]">
    <slot />
  </label>
</template>
