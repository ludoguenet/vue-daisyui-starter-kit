<script setup lang="ts">
// DaisyUI link component
const props = defineProps<{ href: string; tabindex?: number }>();
</script>

<template>
  <a :href="href" :tabindex="tabindex" class="link link-hover underline underline-offset-4">
    <slot />
  </a>
</template>
