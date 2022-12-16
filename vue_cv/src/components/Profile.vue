<!-- eslint-disable vue/multi-word-component-names -->
<script setup lang="ts">
import ContactItem from "./ContactItem.vue";
import GitHubIcon from "./icons/IconGitHub.vue";
import MailIcon from "./icons/IconMail.vue";
import LinkedInIcon from "./icons/IconLinkedIn.vue";
import useClipboard from "vue-clipboard3";
import $ from "jquery";

const { toClipboard } = useClipboard();

const copy = async () => {
  try {
    const mail: string = "victor.sdbustamante@gmail.com";
    await toClipboard(mail);
    $(".mailcopied").css("visibility", "visible");
    console.log("Copied to clipboard", mail);
    await delay(1000);
    $(".mailcopied").css("visibility", "collapse");
  } catch (e) {
    console.error(e);
  }
};

function delay(ms: number) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}

defineProps<{
  msg: string;
}>();
</script>

<template>
  <div class="greetings">
    <h1 class="purple">{{ msg }}</h1>
    <h2 class="gray">Développeur Fullstack</h2>
    <br />
    <h3 class="puple">
      <div class="mail">
        <a id="mail" @click="copy" href="#">victor.sdbustamante@gmail.com</a>
        <div class="mailcopied">Copié !</div>
      </div>
      <div class="contact">
        <a
          class="icon"
          href="mailto:victor.sdbustamante@gmail.com?subject=Prise de contact"
          target="_blank"
        >
          <ContactItem>
            <template #icon>
              <MailIcon />
            </template>
          </ContactItem>
        </a>
        <a class="icon" target="_blank" href="https://github.com/victorbusta">
          <ContactItem>
            <template #icon>
              <GitHubIcon />
            </template>
          </ContactItem>
        </a>
        <a
          class="icon"
          href="https://www.linkedin.com/in/victor-santos-de-bustamante-4906091aa/"
          target="_blank"
        >
          <ContactItem>
            <template #icon>
              <LinkedInIcon />
            </template>
          </ContactItem>
        </a>
      </div>
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h2 {
  font-size: 2rem;
}

.contact {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-content: center;
}

.greetings h1,
.greetings h2 {
  text-align: center;
}

.icon {
  margin-top: 2rem;
  margin-left: 2rem;
  margin-right: 2rem;
  border-radius: 1rem;
}

.mail {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-content: center;
}

.mailcopied {
  position: absolute;
  right: 4rem;
  visibility: collapse;
}

.mail a {
  text-align: center;
  margin: 0 2rem 0 2rem;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h2 {
    text-align: center;
  }
}
</style>
