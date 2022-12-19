<script setup lang="ts">
import WelcomeItem from "./WelcomeItem.vue";
import DevopsIcon from "./icons/IconDevops.vue";
import NodeIcon from "./icons/IconNode.vue";
import SymfonyIcon from "./icons/IconSymfony.vue";
import TypescriptIcon from "./icons/IconTypescript.vue";
import VueIcon from "./icons/IconVue.vue";
</script>

<template>
  <a>
    <WelcomeItem>
      <template #icon>
        <DevopsIcon />
      </template>
      <template #heading>Devops</template>
    </WelcomeItem>
  </a>

  <a
    class="icon"
    href="https://github.com/victorbusta/muzikaloid"
    target="_blank"
  >
    <WelcomeItem>
      <template #icon>
        <SymfonyIcon />
      </template>
      <template #heading>Symfony</template>
    </WelcomeItem>
  </a>

  <a
    class="icon"
    href="https://github.com/victorbusta/rest_api"
    target="_blank"
  >
    <WelcomeItem>
      <template #icon>
        <TypescriptIcon />
      </template>
      <template #heading>TypeScript</template>
    </WelcomeItem>
  </a>

  <a
    class="icon"
    href="https://github.com/victorbusta/rest_api"
    target="_blank"
  >
    <WelcomeItem>
      <template #icon>
        <NodeIcon />
      </template>
      <template #heading>Node Js</template>
    </WelcomeItem>
  </a>
  <a class="icon" href="https://github.com/victorbusta/cv" target="_blank">
    <WelcomeItem>
      <template #icon>
        <VueIcon />
      </template>
      <template #heading>Vue</template>
    </WelcomeItem>
  </a>
</template>
