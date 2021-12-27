<template>
  <div v-show="loaderVisible" class="loader-container">
    <img
      class="logo mb-5 loader"
      alt="logo"
      src="../src/assets/logo-white.svg"
    />
  </div>
  <Login />
</template>

<script>
import Login from "./components/Login.vue";

export default {
  name: "App",
  components: {
    Login,
  },
  data() {
    return {
      loaderVisible: true,
    };
  },

  created() {
    setTimeout(() => (this.loaderVisible = false), 1500);
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  min-height: 100%;
  height: 100%;
  width: 100%;
  /* #dark blue: #0f2640
      button: #2d7ce5
*/
}
.loader-container {
  width: 100%;
  height: 100%;
  background-color: #0f2640;
  position: absolute;
  z-index: 4;
  overflow: hidden;
}
.loader {
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: 10;
  animation: zoom-in ease-in-out 1.5s;
  animation-fill-mode: forwards;
  animation-timing-function: cubic-bezier(0.1, -0.6, 0.2);
  overflow: hidden;
  right: 0px;
}
.hidden {
  display: none;
}
@keyframes zoom-in {
  0% {
    transform: scale(0.6);
  }
  50% {
    transform: scale(0.4);
    opacity: (0.5);
  }
  100% {
    transform: scale(1);
    opacity: 0;
    display: none;
    visibility: hidden;
  }
}
</style>
