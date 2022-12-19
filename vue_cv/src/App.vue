<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import Profile from "./components/Profile.vue";
import $ from "jquery";

const spin = async () => $(".logo").toggleClass("spin");
</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="@/assets/profile-croped.png"
      width="125"
      height="125"
      @click="spin()"
    />

    <div class="wrapper">
      <Profile msg="Victor Santos de Bustamante" />

      <nav>
        <RouterLink to="/">Technologies</RouterLink>
        <!-- <RouterLink to="/about">A propos</RouterLink> -->
      </nav>
    </div>
  </header>
  <main>
    <RouterView />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
  text-align: center;
  filter: drop-shadow(0 0 0.2rem #000000);
}

.corner {
  position: absolute;
  bottom: 0px;
  right: 0px;
  rotate: 90deg;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
  width: 200px;
  height: auto;
}

@keyframes spin3D {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(360deg);
  }
}

.spin {
  animation-name: spin3D;
  animation-duration: 1s;
  animation-iteration-count: 1;
  /* linear | ease | ease-in | ease-out | ease-in-out */
  animation-timing-function: ease-in-out;
}

nav {
  width: 100%;
  font-size: 18px;
  margin-top: 2rem;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

nav a.router-link-exact-active {
  color: var(--color-text-selected);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (max-width: 1024px) {
  main {
    margin-top: 3rem;
  }
}

@media (min-width: 1024px) {
  header {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    /* margin: 0 2rem 0 0; */
    width: 300px;
    height: auto;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
    justify-content: center;
  }

  nav {
    text-align: center;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
