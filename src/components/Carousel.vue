<script>
import { onMounted, ref } from 'vue'
export default {
  name: 'Carousel',
  setup() {
    const currentSlide = ref(1)
    const slidesCount = ref(null)
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
    onMounted(() => {
      slidesCount.value = document.querySelectorAll('.slide').length
    })
    return { currentSlide, prevSlide, nextSlide }
  },
}
</script>

<template>
  <div class="carousel">
    <slot :currentSlide="currentSlide" />
    <!-- navigation carousel -->
    <div class="navigation">
      <div class="toggle-page left">
        <i class="fas fa-chevron-left" @click="prevSlide"></i>
      </div>
      <div class="toggle-page right">
        <i class="fas fa-chevron-right" @click="nextSlide"></i>
      </div>
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
</style>
