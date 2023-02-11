<!-- eslint-disable vue/multi-word-component-names -->
<script setup lang="ts">
import ContactItem from "./ContactItem.vue";
import GitHubIcon from "./icons/IconGitHub.vue";
import MailIcon from "./icons/IconMail.vue";
import LinkedInIcon from "./icons/IconLinkedIn.vue";
import useClipboard from "vue-clipboard3";

const { toClipboard } = useClipboard();

const copy = async () => {
  try {
    await toClipboard("victor.sdbustamante@gmail.com");
    await delay(1000);
  } catch (e) {
    console.error(e);
  }
};

function delay(ms: number) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}
</script>

<template>
  <div class="greetings">
    <img
      alt="Vue logo"
      class="logo"
      src="@/assets/profile-croped.png"
      width="128"
      height="128"
    />
    <h1 class="purple">
      Victor <br />
      Santos de Bustamante
    </h1>
    <h2 class="gray">Développeur Fullstack</h2>
    <a id="mail" @click="copy()">victor.sdbustamante@gmail.com</a>
    <div class="contact">
      <ContactItem
        link="mailto:victor.sdbustamante@gmail.com?subject=Prise de contact"
      >
        <template #icon>
          <MailIcon />
        </template>
      </ContactItem>

      <ContactItem link="https://github.com/victorbusta">
        <template #icon>
          <GitHubIcon />
        </template>
      </ContactItem>

      <ContactItem
        link="https://www.linkedin.com/in/victor-santos-de-bustamante-4906091aa/"
      >
        <template #icon>
          <LinkedInIcon />
        </template>
      </ContactItem>
    </div>
  </div>
</template>

<style scoped>
.greetings {
  display: flex;
  flex-direction: column;
  justify-items: center;
  justify-content: space-evenly;
  align-items: center;
  border-width: 1px;
  border-color: var(--color-background-bis);
  border-style: solid;
  border-radius: 8px;
  height: 100%;
  width: 100%;
}

img {
  margin-top: 8px;
}

h1,
h2 {
  text-align: center;
  margin: 8px;
}

.contact {
  margin: 8px;
}
</style>
