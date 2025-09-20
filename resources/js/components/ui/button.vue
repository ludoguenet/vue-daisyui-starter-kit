<script setup lang="ts">
// DaisyUI button component for UI folder
const props = defineProps<{ type?: 'button' | 'submit' | 'reset'; disabled?: boolean; class?: string }>();
</script>

<template>
  <button :type="props.type ?? 'button'" :disabled="props.disabled" :class="['btn', props.class || 'btn-primary']">
    <slot />
  </button>
</template>
