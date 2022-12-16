<script setup lang="ts">
import WelcomeItem from "./WelcomeItem.vue";
import DocumentationIcon from "./icons/IconSql.vue";
import SymfonyIcon from "./icons/IconSymfony.vue";
import DockerIcon from "./icons/IconDocker.vue";
import TypescriptIcon from "./icons/IconTypescript.vue";
import VueIcon from "./icons/IconVue.vue";
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Base de Données</template>
    Ayant plus que de simples notions en SQL, ainsi qu'ayant déjà travaillé avec
    avec des BDD NoSQL. Je peux aisaiment vous guider vers une solution adapter
    a vos besoins
    <!-- Vue’s
    <a href="https://vuejs.org/" target="_blank" rel="noopener"
      >official documentation</a
    >
    provides you with all information you need to get started. -->
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <DockerIcon />
    </template>
    <template #heading>Administration de systèmes</template>

    This project is served and bundled with
    <a
      href="https://vitejs.dev/guide/features.html"
      target="_blank"
      rel="noopener"
      >Vite</a
    >. The recommended IDE setup is
    <a
      href="https://code.visualstudio.com/"
      target="_blank"
      rel="noopener"
      class="purple"
      >VSCode</a
    >
    +
    <a
      href="https://github.com/johnsoncodehk/volar"
      target="_blank"
      rel="noopener"
      class="purple"
      >Volar</a
    >. If you need to test your components and web pages, check out
    <a
      href="https://www.cypress.io/"
      target="_blank"
      rel="noopener"
      class="purple"
      >Cypress</a
    >
    and
    <a href="https://on.cypress.io/component" target="_blank"
      >Cypress Component Testing</a
    >.

    <br />

    More instructions are available in <code>README.md</code>.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <SymfonyIcon />
    </template>
    <template #heading>Symfony</template>

    Get official tools and libraries for your project:
    <a href="https://pinia.vuejs.org/" target="_blank" rel="noopener">Pinia</a>,
    <a href="https://router.vuejs.org/" target="_blank" rel="noopener"
      >Vue Router</a
    >,
    <a href="https://test-utils.vuejs.org/" target="_blank" rel="noopener"
      >Vue Test Utils</a
    >, and
    <a href="https://github.com/vuejs/devtools" target="_blank" rel="noopener"
      >Vue Dev Tools</a
    >. If you need more resources, we suggest paying
    <a
      href="https://github.com/vuejs/awesome-vue"
      target="_blank"
      rel="noopener"
      >Awesome Vue</a
    >
    a visit.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <TypescriptIcon />
    </template>
    <template #heading>Type Script</template>

    Got stuck? Ask your question on
    <a href="https://chat.vuejs.org" target="_blank" rel="noopener">Vue Land</a
    >, our official Discord server, or
    <a
      href="https://stackoverflow.com/questions/tagged/vue.js"
      target="_blank"
      rel="noopener"
      >StackOverflow</a
    >. You should also subscribe to
    <a href="https://news.vuejs.org" target="_blank" rel="noopener"
      >our mailing list</a
    >
    and follow the official
    <a href="https://twitter.com/vuejs" target="_blank" rel="noopener"
      >@vuejs</a
    >
    twitter account for latest news in the Vue world.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <VueIcon />
    </template>
    <template #heading>Vue</template>

    <a href="https://github.com/victorbusta/cv"></a>
  </WelcomeItem>
</template>
