<template>
  <div id="app">
    <h1>Carrinho de Compras </h1>
    <ProductList @add-to-cart="addToCart" />
    <Cart :cart="cart" @remove-from-cart="removeFromCart" />
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue';

export default {
  components: {
    ProductList,
  },
  data() {
    return {
      cart: [],
    };
  },
  methods: {
    addToCart(product) {
      const item = this.cart.find(item => item.id === product.id);
      if (item) {
        item.quantity++;
      } else {
        this.cart.push({ ...product, quantity: 1 });
      }
    },
    removeFromCart(productId) {
      this.cart = this.cart.filter(item => item.id !== productId);
    },
  },
};
</script>
