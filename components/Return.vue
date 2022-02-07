<template>
  <NuxtLink :to="to" class="rounded-btn">
    <font-awesome-icon icon="arrow-left" size="2x" />
  </NuxtLink>
</template>

<script>
export default {
  name: 'Return',
  props: {
    to: {type: String, default: '/'},
  },
}
</script>

<style lang="scss">
  .rounded-btn {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
    margin: 1rem;
    padding: 13px;
    padding-inline: 16px;
    border-radius: 100%;
    background-color: rgba(255, 255, 255, 0.877);
    color: rgb(42, 80, 95);
    box-shadow: 6px 5px 6px rgba(0, 0, 0, 0.452);
  }
</style>