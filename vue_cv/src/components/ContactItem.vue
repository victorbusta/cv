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
.item {
  width: 48px;
  height: 48px;
  display: flex;
  justify-content: center;
  align-content: center;
  border: 1px;
  border-style: solid;
}

a {
  width: 48px;
  height: 48px;
  margin: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  border-radius: 16px;
  background: #2a2d34;
  box-shadow: 5px 5px 10px #1d1f24, -5px -5px 10px #373b44;
}

a:active {
  box-shadow: inset 5px 5px 10px #1d1f24, inset -5px -5px 10px #373b44;
}
</style>
