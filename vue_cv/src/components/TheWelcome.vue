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
      <template #content
        >Il est indispensable de pouvoir assurer des tests unitaires,
        automatiser la mise en production et soigner l'environnement de
        developpement d'un projet.
      </template>
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
      <template #content>Voir un projet utilisant Symfony! </template>
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
      <template #content>Voir un projet utilisant TypeScript </template>
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
      <template #content>Voir un projet utilisant Node! </template>
    </WelcomeItem>
  </a>

  <a class="icon" href="https://github.com/victorbusta/cv" target="_blank">
    <WelcomeItem>
      <template #icon>
        <VueIcon />
      </template>
      <template #heading>Vue</template>
      <template #content>Voir un projet utilisant Vue! </template>
    </WelcomeItem>
  </a>
</template>

<style scoped>
@media (max-width: 1024px) {
  a {
    width: 100%;
    margin-bottom: 2rem;
    border-radius: 8px;
  }
}
</style>
