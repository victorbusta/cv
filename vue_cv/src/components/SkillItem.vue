<script setup lang="ts">
defineProps<{
  link: string;
}>();
</script>

<template>
  <div class="content">
    <div class="header">
      <i>
        <slot name="icon"></slot>
      </i>
      <h2>
        <slot name="heading" ref="heading"></slot>
      </h2>
    </div>
    <a v-bind:href="link" target="_blank">
      <p>
        <slot name="content"></slot>
      </p>
    </a>
  </div>
</template>

<style scoped>

</style>
