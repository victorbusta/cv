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

  anim.translate("nav", "0px", "0px");
  anim.resize("nav", "384px", "384px");

  openLinks();
}

async function closeNav() {
  closeBuger();
  closeLinks();

  await anim.delay(300);

  anim.translate("nav", "24px", "24px");
  anim.resize("nav", "256px", "256px");
}

async function openLinks() {
  const links = document.querySelectorAll(".link");

  var angle = 0;

  links.forEach(async (link) => {
    anim.translateEl(link, "96px", "-96px");

    await anim.delay(300);

    // anim.hideEl(link, false, 0);
    anim.rotateEl(link, `${angle}deg`);
    angle += 25;
  });

  await anim.delay(300);
}

async function closeLinks() {
  const links = document.querySelectorAll(".link");

  links.forEach(async (link) => {
    anim.rotateEl(link, "0deg");

    await anim.delay(300);

    // anim.hideEl(link, true, 0);
    anim.translateEl(link, "64px", "-160px");
  });

  await anim.delay(300);
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
  <div class="burger" @click="navAnimation">
    <span class="line line1"></span>
    <span class="line line2"></span>
    <span class="line line3"></span>
  </div>
  <nav @click="navAnimation">
    <!-- <div class="link link0"></div> -->
    <div class="link link1">
      <RouterLink :to="{ name: 'contact' }"><h3>Contact</h3></RouterLink>
    </div>
    <div class="link link2">
      <RouterLink :to="{ name: 'skills' }"><h3>Compétences</h3></RouterLink>
    </div>
    <div class="link link3">
      <RouterLink :to="{ name: 'about' }"><h3>Présentation</h3></RouterLink>
    </div>
  </nav>

  <!-- <div class="index"><h1 class="head">Contact</h1></div> -->

  <content>
    <div class="view"><RouterView /></div>
  </content>
</template>

<style scoped>
.index {
  grid-row: 2;
  grid-column: 2;
  width: 100%;
  height: 100%;
  z-index: -1;
}

h1 {
  text-align: center;
}

content {
  grid-row: 2;
  grid-column: 2;
  width: 100%;
  height: 100%;
  display: grid;
  justify-items: center;
  align-items: center;
  z-index: 1;
}

div .view {
  width: calc(100% - 20px);
  height: calc(100% - 20px);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

nav {
  position: fixed;
  display: grid;
  /* width: 256px;
  height: 256px; */
  top: -152px;
  left: -152px;
  border-radius: 50%;
  /* background-color: var(--color-background); */
  align-items: center;
  transform: translate(24px, 24px);
  z-index: 2;
  /* transition: all 0.5s cubic-bezier(1, -1.03, 0, 1.92); */
}

.link {
  position: fixed;
  height: 192px;
  width: 192px;
  border-radius: 0 198px 0 0;
  top: 96px;
  left: 96px;
  opacity: 1;
  text-align: center;
  transform: translate(64px, -160px);
}

.link a {
  width: 100%;
  height: 100%;
  right: 0;
  border-radius: 0 100% 0 0;
  position: absolute;
  z-index: 1;
}

/* .link0 {
  z-index: 5;
  background-color: var(--color-background);
  height: 193px;
  width: 193px;
} */
.link1 {
  z-index: 4;
  background-color: var(--color-nav);
}
.link2 {
  z-index: 3;
  background-color: var(--color-nav-bis);
}
.link3 {
  z-index: 2;
  background-color: var(--color-nav-ter);
}

h3 {
  position: absolute;
  bottom: 0;
  width: 160px;
  right: 0px;
  color: var(--color-background);
}

div .burger {
  position: fixed;
  width: 48px;
  height: 48px;
  /* background-color: var(--color-background); */
  border-radius: 50%;
  top: 16px;
  left: 16px;
  opacity: 1;
  display: grid;
  align-items: center;
  z-index: 5;
}

.line {
  position: absolute;
  height: 4px;
  width: 100%;
  border-radius: 4px;
  display: block;
  background-color: var(--color-background-bis);
}

.line1 {
  transform: translateY(16px);
}

.line3 {
  transform: translateY(-16px);
}
</style>
