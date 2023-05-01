<template>
  <div class="wrapper">
    <h1>Products</h1>

    <div class="card-container">
      <ProductCard
        v-for="product in inventory"
        :key="product.id"
        :product="product"
        :add-to-cart="addToCart"
      />
    </div>
  </div>
</template>

<script>
import ProductCard from "@/components/ProductCard.vue";

export default {
  components: { ProductCard },
  props: ["inventory", "addToCart"],
};
</script>
