<template>
  <div class="splash-container">
    <div class="splash">
      <h1>Splendid Food</h1>
    </div>
  </div>

  <div class="wrapper">
    <h2>Recommended</h2>

    <div class="recommended">
      <div
        class="card"
        v-for="product in inventory.slice(0, 3)"
        :key="product.id"
      >
        <div class="card-title">
          {{ product.name }}
        </div>
        <div class="card-body">
          <i :class="['icofont-10x', `icofont-${product.icon}`]"></i>
          <form>
            <div class="row">
              <div class="cell">
                <label>Type:</label>
              </div>
              <div class="cell">
                <em>{{
                  `${product.type[0].toUpperCase()}${product.type.slice(1)}`
                }}</em>
              </div>
            </div>
            <div class="row">
              <div class="cell">
                <label>Price:</label>
              </div>
              <div class="cell">${{ product.price.USD }}</div>
            </div>
            <div class="row">
              <div class="cell">
                <label>Quantity:</label>
              </div>
              <div class="cell">
                <input type="number" v-model.number="product.quantity" />
              </div>
            </div>
          </form>
        </div>
        <div class="card-footer">
          <button @click="addToCart(product)" class="btn btn-light">
            Add to cart
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import food from "../food.json";

export default {
  name: "HomeView",
  components: {},
  data() {
    return {
      inventory: food.map((product) => ({ ...product, quantity: 0 })),
      // cart: {},
      // showCart: false,
    };
  },
};
</script>
