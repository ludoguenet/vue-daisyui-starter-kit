<script setup lang="ts">
const props = defineProps<{ id?: string; name?: string; checked?: boolean; tabindex?: number }>();
</script>
<template>
  <input
    type="checkbox"
    :id="props.id"
    :name="props.name"
    :checked="props.checked"
    :tabindex="props.tabindex"
    class="checkbox"
  />
</template>
