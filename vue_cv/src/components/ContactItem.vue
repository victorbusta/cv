<script setup lang="ts">
import $ from "jquery";

var opened = 0;
var iconElement = new EventTarget();

const hoveringIcon = (event: Event) => {
  if (opened === 0 && event.currentTarget !== null) {
    opened = 1;
    iconElement = $(event.target);
    console.log(iconElement);

    $(iconElement).animate({
      rotate: "360deg",
    });
  }
};

const exitingCard = (event: Event) => {
  if (opened === 1 && event.currentTarget !== null) {
    opened = 0;
    $(iconElement).animate({
      rotate: "0deg",
    });
  }
};
</script>

<template>
  <div class="item">
    <i @mouseleave="exitingCard($event)" @mouseover="hoveringIcon($event)">
      <slot name="icon"></slot>
    </i>
  </div>
</template>

<style scoped>
i {
  display: flex;
  place-items: center;
  place-content: center;
  width: 32px;
  height: 32px;
  color: var(--color-text);
  margin: 1rem;
  transition: transform 1.5s ease;
  transition: all 1.5 ease;
}

.spin {
  transform: rotateY(360deg);
}

@media (min-width: 1024px) {
  i {
    top: calc(50% - 25px);
    position: relative;
    border: 1px solid var(--color-border);
    background: var(--color-background);
    border-radius: 8px;
    width: 50px;
    height: 50px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
  }
}
</style>
