<template>
  <div class="slide">
    <transition name="slide">
      <slot />
    </transition>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.slide-enter-active,
.slide-leave-active {
  transition: opacity 0.7s ease-in-out;
  animation: zoomin 16s infinite;
}

.slide-enter-from,
.slide-leave-to {
  opacity: 0;
}
.slide-enter-to,
.slide-leave-from {
  opacity: 1;
}

@keyframes zoomin {
  0% {
    transform: scale(1.1);
  }
  100% {
    transform: scale(1.3);
  }
}
</style>
