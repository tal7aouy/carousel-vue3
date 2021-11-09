<script>
import { onMounted, ref } from 'vue'
export default {
  name: 'Carousel',
  props: ['navigation', 'timeDuration', 'pagination', 'startAutoPlay'],
  setup(props) {
    const currentSlide = ref(1)
    const slidesCount = ref(null)
    const autoPlay = ref(
      props.startAutoPlay === undefined ? true : props.startAutoPlay
    )
    const timeDuration = ref(
      props.timeDuration === undefined ? 4000 : props.timeDuration
    )
    const paginationEnabled = ref(
      props.pagination === undefined ? true : props.pagination
    )
    const navigationEnabled = ref(
      props.navigation === undefined ? true : props.navigation
    )
    // next slider
    function nextSlide() {
      if (currentSlide.value === slidesCount.value) {
        currentSlide.value = 1
        return
      }
      currentSlide.value += 1
    }
    // Previous slider
    function prevSlide() {
      if (currentSlide.value === 1) {
        currentSlide.value = 1
        return
      }
      currentSlide.value -= 1
    }
    // paginate to slide
    function toSlide(index) {
      currentSlide.value = index + 1
    }
    // autoPlay carousel
    function autoPlaySlider() {
      setInterval(() => {
        nextSlide()
      }, timeDuration.value)
    }
    if (autoPlay.value) {
      autoPlaySlider()
    }
    onMounted(() => {
      slidesCount.value = document.querySelectorAll('.slide').length
    })
    return {
      currentSlide,
      prevSlide,
      nextSlide,
      slidesCount,
      toSlide,
      autoPlaySlider,
      paginationEnabled,
      navigationEnabled,
    }
  },
}
</script>

<template>
  <div class="carousel">
    <slot :currentSlide="currentSlide" />
    <!-- navigation carousel -->
    <div v-if="navigationEnabled" class="navigation">
      <div class="toggle-page left">
        <i class="fas fa-chevron-left" @click="prevSlide"></i>
      </div>
      <div class="toggle-page right">
        <i class="fas fa-chevron-right" @click="nextSlide"></i>
      </div>
    </div>
    <!-- Pagination -->
    <div v-if="paginationEnabled" class="pagination">
      <span
        v-for="(slide, index) in slidesCount"
        :key="index"
        :class="{ active: currentSlide === index + 1 }"
        @click="toSlide(index)"
      >
      </span>
    </div>
  </div>
</template>
<style scoped>
.navigation {
  padding: 0 16px;
  height: 100%;
  width: 100%;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}
.toggle-page {
  display: flex;
  flex: 1;
}
.right {
  justify-content: flex-end;
}
i {
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  background-color: #6347fe;
  color: white;
}
.pagination {
  position: absolute;
  bottom: 24px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 16px;
}
.pagination span {
  cursor: pointer;
  width: 15px;
  height: 15px;
  border-radius: 50%;
  background-color: #95a69e;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
}
span.active {
  background-color: #6347fe;
}
</style>
