<template>
  <div>
    <Carousel :navigation="true" class="carousel" v-slot="{ currentSlide }">
      <Slide v-for="(slide, index) in carouselSlides" :key="index">
        <div v-show="currentSlide === index + 1" class="slide-info">
          <img :src="slide" alt="" />
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
  setup() {
    const carouselSlides = [
      '/images/1.jpg',
      '/images/2.jpg',
      '/images/3.jpg',
      '/images/4.jpg',
    ]
    return {
      carouselSlides,
    }
  },
}
</script>

<style scoped>
.carousel {
  position: relative;
  max-height: 100vh;
  height: 100vh;
}
.slide-info {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  width: 100%;
  max-height: 100%;
  height: 100%;
}
img {
  min-width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
