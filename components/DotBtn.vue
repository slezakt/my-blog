<template>
  <button :class="['embla__dot', { 'is-selected': selected }]" @click="$emit('click')"></button>
</template>

<script>
export default {
  props: ["selected"]
};
</script>