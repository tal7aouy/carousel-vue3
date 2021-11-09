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
