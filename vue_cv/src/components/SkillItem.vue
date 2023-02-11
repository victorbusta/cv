<script setup lang="ts">
defineProps<{
  link: string;
}>();

// function seeSkill(e: any) {
//   console.log(e.target?.parentElement);
// }
</script>

<template>
  <div class="content">
    <!-- <div class="overheader" @click="seeSkill($event)"></div> -->
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
.content {
  width: 100%;
  border-width: 1px;
  border-color: var(--color-background-bis);
  border-style: solid;
  border-radius: 8px;
}

.header {
  display: grid;
  grid-template-columns: 80px calc(100% - 80px);
  justify-items: center;
  align-items: center;
}

i {
  width: 64px;
  height: 64px;
  margin: 8px;
}

p {
  color: var(--color-text);
  /* height: 0px; */
  border-top: 1px;
  border-color: var(--color-background-bis);
  border-top-style: solid;
  border-radius: 0px 0px 7px 7px;
  margin: 8px;
}

a:hover p {
  background-color: var(--color-background-bis);
}
</style>
