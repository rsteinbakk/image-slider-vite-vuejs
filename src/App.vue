

<template>
  <div class="swiper-outer-container">
    <div class="swiper-size">
      <ImageSlider :products="products"/>
    </div>
  </div>
</template>
<script>
import ImageSlider from "./components/ImageSlider.vue";
export default {
  components: {
    ImageSlider,
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    getImages() {
      fetch("https://fakestoreapi.com/products?limit=5")
        .then((res) => res.json())
        .then((data) => (this.products = data));
    },
  },
  created() {
    this.getImages();
  },
};
</script>
<style>
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 50px;
}
.swiper-outer-container {
  display: flex;
  justify-content: center;
}
.swiper-size {
  max-width: 310px;
  max-height: 350px;
  border: 3px solid black;
}
</style>
