<script setup lang="ts">
defineProps<{
  link: string;
}>();
</script>

<template>
  <a v-bind:href="link" target="_blank">
    <slot name="icon"></slot>
  </a>
</template>

<style scoped>
a {
  margin: 8px;
  height: 100%;
  width: 100%;
}
</style>
