<script setup lang="ts">
const props = defineProps<{ type?: string; name?: string; id?: string; value?: string; placeholder?: string; class?: string; required?: boolean; autofocus?: boolean; autocomplete?: string; tabindex?: number }>();
</script>
<template>
  <input
    :type="props.type ?? 'text'"
    :name="props.name"
    :id="props.id"
    :value="props.value"
    :placeholder="props.placeholder"
    :class="['input input-bordered w-full', props.class]"
    :required="props.required"
    :autofocus="props.autofocus"
    :autocomplete="props.autocomplete"
    :tabindex="props.tabindex"
  />
</template>
