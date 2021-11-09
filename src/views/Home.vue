<template>
  <div>
    <Carousel class="carousel">
      <Slide>
        <div>
          <h2>Hello slider</h2>
        </div>
      </Slide>
    </Carousel>
  </div>
</template>

<script>
import Carousel from '@/components/Carousel.vue'
import Slide from '@/components/Slide.vue'
export default {
  name: 'Home',
  components: {
    Carousel,
    Slide,
  },
}
</script>

<style scoped>
.carousel {
  max-height: 100vh;
  height: 100vh;
}
</style>
