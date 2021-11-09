<script>
export default {
  name: 'Slide',
}
</script>
<template>
  <div class="slide">
    <transition name="slide">
      <slot />
    </transition>
  </div>
</template>

<style scoped>
.slide-enter-active,
.slide-leave-active {
  transition: opacity 250ms ease-in-out;
}
.slide-enter-from,
.slide-leave-to {
  opacity: 0;
}
.slide-enter-to,
.slide-leave-from {
  opacity: 1;
}
</style>
