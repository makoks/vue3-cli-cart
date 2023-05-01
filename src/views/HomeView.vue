<template>
  <div class="splash-container">
    <div class="splash">
      <h1>Splendid Food</h1>
    </div>
  </div>

  <div class="wrapper">
    <h2>Recommended</h2>

    <div class="recommended">
      <ProductCard
        v-for="product in inventory.slice(0, 3)"
        :key="product.id"
        :product="product"
        :add-to-cart="addToCart"
      />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import ProductCard from "@/components/ProductCard.vue";

export default {
  name: "HomeView",
  components: { ProductCard },
  props: ["inventory", "addToCart"],
};
</script>
