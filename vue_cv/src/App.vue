<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";

const navRadius = 64;

var opened = false;
var lastPos = 0;

const showNav = async () => {
  if (window.innerWidth <= 768) {
    const linkElements = Array.from(document.querySelectorAll("nav > a"));

    if (opened) {
      closeNav(linkElements);
    } else {
      openNav(linkElements);
    }
    opened = !opened;
  }
};

function closeNav(linkElements: Element[]) {
  lastPos = 0;

  openBurger();

  linkElements.forEach(async (element) => {
    element.animate(
      [
        {
          transform: `translate(${
            2 * navRadius * Math.cos(degToRad(lastPos)) - 64
          }px)`,
        },
      ],
      {
        duration: 100,
        fill: "forwards",
      }
    );
    element.animate([{ opacity: 0 }], {
      duration: 300,
      fill: "forwards",
    });
    await delay(100);
    element.animate([{ transform: "translate(0)" }], {
      duration: 100,
      fill: "forwards",
    });
  });
}

function openNav(linkElements: Element[]) {
  lastPos = 0;

  closeBurger();

  linkElements.forEach(async (element) => {
    element.animate(
      [
        {
          transform: `translateX(${
            2 * navRadius * Math.cos(degToRad(lastPos)) - 64
          }px)`,
        },
      ],
      {
        duration: 100,
        fill: "forwards",
      }
    );

    element.animate([{ opacity: 1 }], {
      duration: 300,
      fill: "forwards",
    });

    await delay(100);

    element.animate(
      [
        {
          transform: `translate(${
            2 * navRadius * Math.cos(degToRad(lastPos)) - 64
          }px, -${2 * navRadius * Math.sin(degToRad(lastPos))}px)
    rotate(-${lastPos}deg)`,
        },
      ],
      {
        duration: 300,
        fill: "forwards",
      }
    );

    lastPos += 35;
  });
}

function closeBurger() {
  document.querySelector(".line1")?.animate([{ opacity: 0 }], {
    duration: 100,
    fill: "forwards",
  });
  document.querySelector(".line2")?.animate([{ rotate: "45deg" }], {
    duration: 300,
    fill: "forwards",
  });
  document.querySelector(".line3")?.animate(
    [
      {
        transform: `translate(0px, -11px)
    rotate(-45deg)`,
      },
    ],
    {
      duration: 300,
      fill: "forwards",
    }
  );
}

function openBurger() {
  document.querySelector(".line1")?.animate([{ opacity: 1 }], {
    duration: 300,
    fill: "forwards",
  });
  document.querySelector(".line2")?.animate([{ rotate: "0deg" }], {
    duration: 100,
    fill: "forwards",
  });
  document.querySelector(".line3")?.animate(
    [
      {
        transform: `translate(0px)
    rotate(0)`,
      },
    ],
    {
      duration: 100,
      fill: "forwards",
    }
  );
}

const degToRad = (deg: number) => deg * (Math.PI / 180);

function delay(ms: number) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}
</script>

<template>
  <nav>
    <RouterLink to="/" @click="showNav()"><h2>Contact</h2></RouterLink>
    <RouterLink to="/skills" @click="showNav()"
      ><h2>Compétences</h2></RouterLink
    >
    <RouterLink to="/about" @click="showNav()"
      ><h2>Présentation</h2></RouterLink
    >
    <div class="burger" @click="showNav()">
      <span class="line line1"></span>
      <span class="line line2"></span>
      <span class="line line3"></span>
    </div>
  </nav>

  <content>
    <RouterView />
  </content>
</template>

<style scoped>
.blur {
  z-index: 0;
  filter: blur(2px);
}

h2 {
  margin-left: 10px;
  margin-right: 10px;
}

div {
  display: none;
}

content {
  height: auto;
  width: fit-content;
  margin: 10px 10px;
  grid-row: 2;
  justify-content: center;
  align-items: center;
  display: flex;
  flex-direction: column;
}

nav {
  position: fixed;
  z-index: 1;
  height: 3rem;
  top: 0;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  column-gap: 0.875rem;
  /* transition: left 1s ease; */
}

nav a {
  position: relative;
  text-align: center;
  background: #2a2d34;
  border-radius: 16px;
  background: #2a2d34;
  box-shadow: 4px 4px 7px #1d1f24, -4px -4px 7px #373b44;
}

nav a:active {
  box-shadow: inset 4px 4px 7px #1d1f24, inset -4px -4px 7px #373b44;
}

.router-link-active {
  background: #2a2d34;
  box-shadow: inset 4px 4px 7px #1d1f24, inset -4px -4px 7px #373b44;
}

@media screen and (min-width: 768px) {
  nav a {
    opacity: 1;
  }
}

@media screen and (max-width: 768px) {
  nav {
    position: fixed;
    display: grid;
    grid-template-columns: 100%;
    grid-gap: 0px;
    top: 90%;
    width: 75px;
    z-index: 1;
  }

  .navhider {
    grid-row: 1;
    grid-column: 1;
    display: block;
    height: 140%;
    width: 100%;
    background: #2a2d34;
    z-index: 1;
  }

  nav a {
    width: max-content;
    grid-row: 1;
    grid-column: 1;
    opacity: 0;
    text-align: center;
    z-index: 0;
    left: 32px;
  }

  div .burger {
    grid-row: 1;
    grid-column: 1;
    right: 18px;
    display: flex;
    flex-direction: column;
    align-items: center;
    align-content: center;
    justify-items: center;
    justify-content: center;
    border-radius: 128px;
    background: #2a2d34;
    box-shadow: 6px 6px 13px #1d1f24, -6px -6px 13px #373b44;
    height: 64px;
    width: 64px;
    left: 2px;
    z-index: 2;
  }

  div .burger:active {
    box-shadow: inset 6px 6px 13px #1d1f24, inset -6px -6px 13px #373b44;
  }

  .line {
    height: 5px;
    width: 32px;
    background-color: #ebebeba3;
    border-radius: 3px;
    margin: 3px;
    filter: drop-shadow(0 0 0.1rem #000000);
  }
}
</style>
