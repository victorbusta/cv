<script setup lang="ts">
import $ from "jquery";

var opened = 0;
var iconElement = new EventTarget();
var titleElement = new EventTarget();

const hoveringIcon = (event: Event) => {
  if (opened === 0 && event.currentTarget !== null) {
    opened = 1;
    iconElement = $(event.target).children(".item");
    titleElement = $(iconElement).prev();

    if ($(window).width() > 1024)
      $(iconElement).animate({
        left: "10rem",
      });

    $(titleElement).animate({
      opacity: "1",
    });
  }
};

const exitingCard = (event: Event) => {
  if (
    opened === 1 &&
    event.currentTarget !== null &&
    $(window).width() > 1024
  ) {
    opened = 0;
    $(iconElement).animate({
      left: "0rem",
    });
    $(titleElement).animate({
      opacity: "0",
    });
  }
};
</script>

<template>
  <div
    class="hole"
    @mouseleave="exitingCard($event)"
    @mouseover="hoveringIcon($event)"
  >
    <h3>
      <slot name="heading" ref="heading"></slot>
    </h3>
    <div class="item">
      <i>
        <slot name="icon"></slot>
      </i>
      <div class="details">
        <p>
          <slot name="content"></slot>
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
h3 {
  position: relative;
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--color-heading);
  opacity: 0;
}

p {
  display: none;
}

@media (max-width: 1024px) {
  .hole {
    width: 100%;
    height: 160px;
    position: relative;
  }

  h3 {
    opacity: 1;
    top: 0;
    left: 3rem;
    z-index: 1;
  }

  .item {
    top: 0;
    position: absolute;
    width: 100%;
    height: 160px;
    border: 1px solid var(--color-border);
    background: var(--color-background);
    border-radius: 8px;
    filter: drop-shadow(0 0 0.15rem #000000);
  }

  i {
    width: 32px;
    height: 32px;
    color: var(--color-text);
  }
  .details {
    width: 100%;
    height: 115px;
  }

  p {
    display: block;
  }

  .details {
    flex: 1;
    margin: 0 1rem 0 1rem;
    width: calc(100% - (1rem * 2));
    transition: all 1.5 ease;
  }
}

@media (min-width: 1024px) {
  .hole {
    width: calc((100vw / 2) - 2rem);
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    position: relative;
  }
  .item {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 4rem;
    margin: 2rem;
    border: 1px solid var(--color-border);
    background: var(--color-background);
    border-radius: 8px;
    width: 100px;
    height: 100px;
    filter: drop-shadow(0 0 0.2rem #000000);
  }

  i {
    width: 100px;
    height: 100px;
    display: flex;
    place-items: center;
    place-content: center;
    color: var(--color-text);
  }

  h3 {
    position: absolute;
    opacity: 0;
  }

  .details {
    flex: 1;
    margin-left: 1rem;
    transition: all 1.5 ease;
  }
}
</style>
