<script setup lang="ts">
// DaisyUI button component
const props = defineProps<{ type?: 'button' | 'submit' | 'reset'; disabled?: boolean; variant?: string }>();
</script>

<template>
  <button :type="type ?? 'button'" :disabled="disabled" :class="['btn', class || 'btn-primary']">
    <slot />
  </button>
</template>
