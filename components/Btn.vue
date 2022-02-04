<template>
  <button class="button">
    <slot/>
  </button>
</template>

<style lang="scss">
  .button {
    background: $green;
    color: white;
    @include bold-text;
    @include generic-btn;
    &:hover {
      background: $green-dark;
    }
  }
</style>