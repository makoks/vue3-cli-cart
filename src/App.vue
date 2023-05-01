<template>
  <header class="top-bar spread">
    <nav class="top-bar-nav">
      <router-link to="/" class="top-bar-link">
        <i class="icofont-spoon-and-fork"></i>
        <span>Home</span>
      </router-link>
      <router-link to="/products" class="top-bar-link">
        <span>Products</span>
      </router-link>
      <router-link to="/past-orders" class="top-bar-link">
        <span>Past Orders</span>
      </router-link>
    </nav>
    <a @click="toggleShowCart" class="top-bar-cart-link">
      <i class="icofont-cart-alt icofont-1x"></i>
      <span>Cart ({{ cartItemsCount }})</span>
    </a>
  </header>
  <main>
    <router-view :inventory="inventory" :add-to-cart="addToCart" />
  </main>
  <footer></footer>
  <CartComponent
    v-show="showCart"
    :toggle-show="toggleShowCart"
    :cart="cart"
    :remove-product="removeProduct"
  />
</template>

<script>
import food from "@/food.json";
import CartComponent from "./components/CartComponent.vue";

export default {
  components: {
    CartComponent,
  },
  data() {
    return {
      inventory: food.map((product) => ({ ...product, quantity: 0 })),
      cart: {},
      showCart: false,
    };
  },
  methods: {
    addToCart(product, quantity) {
      if (quantity === 0) {
        return;
      }
      if (!this.cart[product.name]) {
        this.cart[product.name] = {
          name: product.name,
          price: product.price.USD,
          icon: product.icon,
          quantity,
        };
      } else {
        this.cart[product.name].quantity += quantity;
      }
    },
    toggleShowCart() {
      this.showCart = !this.showCart;
    },
    removeProduct(name) {
      delete this.cart[name];
    },
  },
  computed: {
    cartItemsCount() {
      return Object.values(this.cart).reduce(
        (sum, { quantity }) => sum + quantity,
        0
      );
    },
  },
};
</script>
