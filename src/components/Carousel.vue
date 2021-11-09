<script>
import { ref } from 'vue'
export default {
  name: 'Carousel',
  setup() {
    const currentSlide = ref(1)
    return { currentSlide }
  },
}
</script>

<template>
  <div class="carousel">
    <slot :currentSlide="currentSlide" />
  </div>
</template>
