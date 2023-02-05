<script setup lang="ts">
import SkillItem from "./SkillItem.vue";
import DevopsIcon from "./icons/IconDevops.vue";
import NodeIcon from "./icons/IconNode.vue";
import SymfonyIcon from "./icons/IconSymfony.vue";
import TypescriptIcon from "./icons/IconTypescript.vue";
import VueIcon from "./icons/IconVue.vue";
</script>

<template>
  <SkillItem link="">
    <template #icon>
      <DevopsIcon />
    </template>
    <template #heading>Devops</template>
    <template #content
      >Il est indispensable de pouvoir assurer des tests unitaires, automatiser
      la mise en production et soigner l'environnement de developpement d'un
      projet.
    </template>
  </SkillItem>

  <SkillItem link="https://github.com/victorbusta/muzikaloid">
    <template #icon>
      <SymfonyIcon />
    </template>
    <template #heading>Symfony</template>
    <template #content>Voir un projet utilisant Symfony! </template>
  </SkillItem>

  <SkillItem link="https://github.com/victorbusta/rest_api">
    <template #icon>
      <TypescriptIcon />
    </template>
    <template #heading>TypeScript</template>
    <template #content>Voir un projet utilisant TypeScript </template>
  </SkillItem>

  <SkillItem link="https://github.com/victorbusta/rest_api">
    <template #icon>
      <NodeIcon />
    </template>
    <template #heading>Node Js</template>
    <template #content>Voir un projet utilisant Node! </template>
  </SkillItem>

  <SkillItem link="https://github.com/victorbusta/cv">
    <template #icon>
      <VueIcon />
    </template>
    <template #heading>Vue</template>
    <template #content>Voir un projet utilisant Vue! </template>
  </SkillItem>
</template>

<style scoped></style>
