<template>
  <div class="item">
    <i>
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
