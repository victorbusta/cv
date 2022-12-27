<script setup lang="ts">
import $ from "jquery";
import { watch } from "vue";

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
.hole {
  width: calc((100vw / 2) - 2rem);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
}

.item {
  margin: 4rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.details {
  flex: 1;
  margin-left: 1rem;
  transition: all 1.5 ease;
}

i {
  display: flex;
  place-items: center;
  place-content: center;
  width: 32px;
  height: 32px;
  color: var(--color-text);
}

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
  h3 {
    opacity: 1;
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
    justify-content: center;
    align-items: center;
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
  }

  h3 {
    position: absolute;
    opacity: 0;
  }
}
</style>
