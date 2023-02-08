<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import * as anim from "./utils/utils.animation";

const diametre = 64;
const bubbleDiameter = 384;

var navLinks: Element[];
var navOpened = false;
var position = 0;

function navigate() {
  navLinks = Array.from(document.querySelectorAll("nav > a"));
  if (!navOpened) {
    openNav();
  } else {
    closeNav();
  }

  navOpened = !navOpened;
}

function openNav() {
  position = 0;
  openBurger();
  openBubble();
  navLinks.forEach(async (el) => {
    anim.translateEl(el, "64px", "0px");
    await anim.delay(150);
    anim.hideEl(el, false);
    anim.translateEl(
      el,
      `${diametre * Math.cos(anim.degToRad(position))}px`,
      `${diametre * Math.PI * Math.sin(anim.degToRad(position))}px`,
      150
    );
    anim.rotateEl(el, `${position}deg`);
    position += 15;
  });
}

async function closeNav() {
  position = 0;
  closeBurger();
  navLinks.forEach(async (el) => {
    anim.hideEl(el, true, 100);
    anim.translateEl(
      el,
      `${diametre * Math.cos(anim.degToRad(position))}px`,
      `${diametre * Math.PI * Math.sin(anim.degToRad(-position))}px`,
      150
    );
    anim.rotateEl(el, `-${position}deg`);
    await anim.delay(150);
    anim.translateEl(el, "64px", "-56px");
    position += 20;
  });
  await anim.delay(150);

  closeBubble();
}

function openBubble() {
  anim.resize(".navBack", `${bubbleDiameter}px`, `${bubbleDiameter}px`);
  anim.translate(
    ".navBack",
    `-${bubbleDiameter / 2 - (diametre / 2 + 4)}px`,
    `-${bubbleDiameter / 2 - (diametre / 2 + 4)}px`
  );
}

function closeBubble() {
  anim.resize(".navBack", `${diametre}px`, `${diametre}px`);
  anim.translate(".navBack", `+${0}px`, `+${0}px`);
}

async function openBurger() {
  anim.translateY(".line1", "0");
  anim.translateY(".line3", "0");
  anim.hide(".line2", true, 100);
  await anim.delay(150);
  anim.rotate(".line1", "45deg");
  anim.rotate(".line3", "-45deg");
}

async function closeBurger() {
  anim.rotate(".line1", "0deg");
  anim.rotate(".line3", "0deg");
  await anim.delay(150);
  anim.hide(".line2", false);
  anim.translateY(".line1", "-10px");
  anim.translateY(".line3", "10px");
}
</script>

<template>
  <div class="navBack"></div>
  <nav>
    <RouterLink :to="{ name: 'contact' }" @click="navigate"
      ><h3>Contact</h3></RouterLink
    >
    <RouterLink :to="{ name: 'skills' }" @click="navigate"
      ><h3>Compétences</h3></RouterLink
    >
    <RouterLink :to="{ name: 'about' }" @click="navigate"
      ><h3>Présentation</h3></RouterLink
    >
    <div class="burgerContainer">
      <div class="burger" @click="navigate">
        <span class="line line1"></span>
        <span class="line line2"></span>
        <span class="line line3"></span>
      </div>
    </div>
  </nav>

  <content>
    <div class="content"><RouterView /></div>
  </content>
</template>

<style scoped>
content {
  width: 90%;
  display: grid;
  justify-items: center;
  grid-template-rows: 72px calc(100vh - 88px);
}

.content {
  grid-row: 2;
  width: 90%;
  display: grid;
  align-items: center;
}

nav {
  position: fixed;
  top: 4px;
  left: 4px;
  height: 64px;
  width: 64px;
  border-radius: 50%;
  display: grid;
  align-items: center;
  /* justify-items: center; */
  grid-template-columns: 100%;
  grid-gap: 0px;
  z-index: 2;
}

.navBack {
  position: fixed;
  top: 4px;
  left: 4px;
  height: 64px;
  width: 64px;
  border-radius: 50%;
  background: #2a2d34;
  box-shadow: 6px 6px 13px #1d1f24, -6px -6px 13px #373b44;
  z-index: 2;
}

.burgerContainer {
  position: fixed;
  top: 4px;
  left: 4px;
  height: 64px;
  width: 64px;
  border-radius: 50%;
  background: #2a2d34;
  box-shadow: 6px 6px 13px #1d1f24, -6px -6px 13px #373b44;
  display: grid;
  align-items: center;
  justify-items: center;
  grid-template-columns: 100%;
  grid-gap: 0px;
}

nav:active {
  box-shadow: inset 6px 6px 13px #1d1f24, inset -6px -6px 13px #373b44;
}

nav a {
  grid-row: 1;
  grid-column: 1;
  left: 32px;
  position: absolute;
  display: grid;
  width: fit-content;
  align-content: center;
  opacity: 0;
  border-radius: 16px;
  background: #2a2d34;
  box-shadow: 4px 4px 7px #1d1f24, -4px -4px 7px #373b44;
  transform: translate(64px, -56px);
}

nav a:active {
  box-shadow: inset 4px 4px 7px #1d1f24, inset -4px -4px 7px #373b44;
}

h3 {
  margin: 4px 8px 4px 8px;
}

.router-link-active {
  background: #2a2d34;
  box-shadow: inset 4px 4px 7px #1d1f24, inset -4px -4px 7px #373b44;
}

div .burger {
  height: 32px;
  width: 32px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  border-radius: 4px;
  background: #2a2d34;
  z-index: 1;
}

.line {
  height: 16%;
  width: 100%;
  position: absolute;
  background-color: #ebebeba3;
  border-radius: 3px;
}

.line1 {
  transform: translateY(-10px);
}

.line3 {
  transform: translateY(10px);
}
</style>
