<template>
  <div class="card">
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
            <input type="number" v-model.number="quantity" />
          </div>
        </div>
      </form>
    </div>
    <div class="card-footer">
      <button @click="addToCartHandler" class="btn btn-light">
        Add to cart
      </button>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  props: ["product", "addToCart"],
  data() {
    return {
      quantity: 0,
    };
  },
  methods: {
    addToCartHandler() {
      this.addToCart(this.product, this.quantity);
      this.quantity = 0;
    },
  },
};
</script>
