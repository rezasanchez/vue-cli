<template>
  <div id="app" class="container mt-5">
    <h1>IDSHop</h1>
    <price-slider
      :sliderStatus="style.sliderStatus"
      :maximum.sync="maximum"
    ></price-slider>
    <product-list :products="products" :maximum="maximum"></product-list>
  </div>
</template>

<script>
// import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
// eslint-disable-next-line no-unused-vars
import PriceSlider from "./components/PriceSlider.vue";
import ProductList from "./components/ProductList.vue";

export default {
  name: "App",
  data: function () {
    return {
      maximum: 50,
      products: [],
      cart: [],
      sliderStatus: true,
    };
  },
  components: {
    PriceSlider,
    ProductList,
    // FontAwesomeIcon,
  },
  mounted: function () {
    fetch("https://hplussport.com/api/products/order/price")
      .then((response) => response.json())
      .then((data) => {
        this.products = data;
      });
  },
};
</script>
