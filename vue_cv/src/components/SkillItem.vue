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
div .content {
  display: grid;
  grid-template-rows: 32px auto;
  margin-bottom: 64px;
  border-radius: 20px;
}

a {
  margin-top: 10px;
  border-radius: 6px;
  background: #2a2d34;
  box-shadow: 2px 2px 5px #1d1f24, -2px -2px 5px #373b44;
}

a:active {
  box-shadow: inset 2px 2px 5px #1d1f24, inset -2px -2px 5px #373b44;
}

div .content:first-child {
  margin-top: 20px;
}

div .header {
  grid-row: 1;
  display: grid;
  grid-template-columns: 32px 100%;
  justify-items: center;
  align-items: center;
}

i {
  height: 32px;
  width: 32px;
  display: grid;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  background: #2a2d34;
  box-shadow: inset 3px 3px 6px #1d1f24, inset -3px -3px 6px #373b44;
}

h2 {
  text-shadow: 1px;
}

p {
  text-shadow: 1px;

  margin: 5px;
  grid-row: 2;
}
</style>
