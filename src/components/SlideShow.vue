<template>
  <div class="img-gallery">
    <img class="img-fluid" v-bind:src="mainImageSrc" />
  </div>
</template>

<script>
export default {
  name: "Images",
  data() {
    return {
      images: [],
      mainImageSrc: require("../assets/images/fatih-kilic-m1dM7ZXvdMs-unsplash.jpg"),
      imgIndex: -1,
    };
  },
  methods: {},
  created() {
    let self = this;
    this.images = [
      {
        id: "1",
        image: require("../assets/images/krists-luhaers-DSB1MZWsGco-unsplash.jpg"),
      },
      {
        id: "2",
        image: require("../assets/images/laura-nyhuis-0P_pT8ZQKd8-unsplash.jpg"),
      },
      {
        id: "3",
        image: require("../assets/images/michael-maasen-ZY7fuakuXJ0-unsplash.jpg"),
      },
    ];

    setTimeout(function () {
      self.mainImageSrc =
        self.images[Math.floor(Math.random(+1) * self.images.length)].image;
    }, 10000);
  },
};
</script>

<style>
.img-gallery {
  height: 100%;
  overflow: hidden;
  object-fit: cover;
  animation: zoomin 10s infinite;
}
.img-fluid {
  height: 100%;
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
