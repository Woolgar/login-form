<template>
  <div class="carousel">
    <slot :currentSlide="currentSlide" />

    <!-- Navigation -->
    <div v-if="navEnabled" class="navigate">
      <div class="toggle-page left">
        <i @click="prevSlide" class="fas fa-chevron-left"></i>
      </div>
      <div class="toggle-page right">
        <i @click="nextSlide" class="fas fa-chevron-right"></i>
      </div>
    </div>
    <!-- Pagination -->
    <div v-if="paginationEnabled" class="pagination">
      <span
        @click="goToSlide(index)"
        v-for="(slide, index) in getSlideCount"
        :key="index"
        :class="{ active: index + 1 === currentSlide }"
      >
      </span>
    </div>
    <!-- Copyright -->
    <div class="copyright">
      <span> </span>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
export default {
  props: ["enableAutoPlay", "interval", "navigation", "pagination"],
  setup(props) {
    const currentSlide = ref(1);
    const getSlideCount = ref(null);
    const autoPlayEnabled = ref(
      props.enableAutoPlay === undefined ? true : props.enableAutoPlay
    );
    const autoPlayDuration = ref(
      props.interval === undefined ? 5000 : props.interval
    );

    const paginationEnabled = ref(
      props.pagination === undefined ? true : props.pagination
    );

    const navEnabled = ref(
      props.navigation === undefined ? true : props.navigation
    );

    // Next slide
    const nextSlide = () => {
      if (currentSlide.value === getSlideCount.value) {
        currentSlide.value = 1;
        return;
      }
      currentSlide.value += 1;
    };

    // Prev slide
    const prevSlide = () => {
      if (currentSlide.value === 1) {
        currentSlide.value = 1;
        return;
      }
      currentSlide.value -= 1;
    };

    // go to slide
    const goToSlide = (index) => {
      currentSlide.value = index + 1;
    };

    // Autoplay

    const autoPlay = () => {
      setInterval(() => {
        nextSlide();
      }, autoPlayDuration.value);
    };

    if (autoPlayEnabled.value) {
      autoPlay();
    }

    onMounted(() => {
      getSlideCount.value = document.querySelectorAll(".slide").length;
    });

    return {
      currentSlide,
      nextSlide,
      prevSlide,
      getSlideCount,
      goToSlide,
      autoPlay,
      autoPlayEnabled,
      autoPlayDuration,
      paginationEnabled,
      navEnabled,
    };
  },
};
</script>

<style scoped>
.navigate {
  height: 100%;
  width: 100%;
  position: absolute;
  padding: 0 16px;
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
  background-color: purple;
  color: #fff;
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
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #fff;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.006);
}
.pagination .active {
  background-color: purple;
}
</style>
