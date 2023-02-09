<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import * as anim from "./utils/utils.animation";

var opened = false;

function navAnimation() {
  if (!opened) {
    openNav();
  } else {
    closeNav();
  }

  opened = !opened;
}

async function openNav() {
  openBurger();
  // anim.rotate("nav", "45deg");
  anim.translate("nav", "0px", "0px");
  anim.resize("nav", "384px", "384px");
  // openLinks();
  anim.translate(".link", "96px", "-96px");
  await anim.delay(300);
  anim.rotate(".link", "30deg");
  // anim.translate("nav", "16px", "16px");
}

async function closeNav() {
  closeBuger();
  // closeLinks();
  anim.rotate(".link", "0deg");
  await anim.delay(300);
  anim.translate(".link", "64px", "-160px");

  anim.translate("nav", "24px", "24px");
  anim.resize("nav", "256px", "256px");

  // anim.translate("nav", "0px", "0px");
}

async function openBurger() {
  anim.hide(".line2", true);
  anim.translateY(".line1", "0px");
  anim.translateY(".line3", "0px");
  anim.rotate(".burger", "180deg", 450);

  await anim.delay(300);

  anim.rotate(".line1", "45deg", 150);
  anim.rotate(".line3", "-45deg", 150);
}

async function closeBuger() {
  anim.rotate(".line1", "0deg", 150);
  anim.rotate(".line3", "0deg", 150);
  anim.rotate(".burger", "-180deg", 450);

  await anim.delay(300);
  anim.hide(".line2", false);

  anim.translateY(".line1", "16px");
  anim.translateY(".line3", "-16px");
}
</script>

<template>
  <div class="burger">
    <span class="line line1"></span>
    <span class="line line2"></span>
    <span class="line line3"></span>
  </div>
  <nav @click="navAnimation">
    <div class="link">
      <RouterLink :to="{ name: 'contact' }">Contact</RouterLink>
    </div>
    <div class="link">
      <RouterLink :to="{ name: 'skills' }">Compétences</RouterLink>
    </div>
    <div class="link">
      <RouterLink :to="{ name: 'about' }">Présentation</RouterLink>
    </div>
  </nav>

  <content>
    <div class="view"><RouterView /></div>
  </content>
</template>

<style scoped>
content {
  grid-row: 3;
  grid-column: 2;
  width: 100%;
  height: 100%;
  display: grid;
  justify-items: center;
  align-items: center;
  z-index: -1;
}

div .view {
  width: calc(100% - 20px);
  height: calc(100% - 20px);
  display: grid;
  justify-content: center;
  align-items: center;
}

nav {
  position: fixed;
  display: grid;
  width: 256px;
  height: 256px;
  top: -152px;
  left: -152px;
  border-radius: 50%;
  background-color: var(--color-background-bis);
  align-items: center;
  transform: translate(24px, 24px);
  /* transition: all 0.5s cubic-bezier(1, -1.03, 0, 1.92); */
}

.link {
  position: fixed;
  height: 192px;
  width: 193px;
  border-radius: 0 192px 0 0;
  background-color: var(--color-background);
  top: 96px;
  left: 96px;
  z-index: 1;
  text-align: center;
  transform: translate(64px, -160px);
}

.link a {
  width: 100%;
  right: 0;
  position: absolute;
  z-index: 1;
  color: black;
  bottom: 0px;
}

div .burger {
  position: fixed;
  width: 48px;
  height: 48px;
  top: 16px;
  left: 16px;
  display: grid;
  align-items: center;
  z-index: 1;
}

.line {
  position: absolute;
  height: 4px;
  width: 100%;
  border-radius: 4px;
  display: block;
  background-color: var(--color-background);
}

.line1 {
  transform: translateY(16px);
}

.line3 {
  transform: translateY(-16px);
}
</style>
