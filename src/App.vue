<template>
  <div id="app">
    <h1>Carrinho de Compras Simples</h1>
    <ProductList @add-to-cart="addToCart" />
    <ShoppingCart :cart="cart" @remove-from-cart="removeFromCart" />
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue';
import ShoppingCart from './components/ShoppingCart.vue';

export default {
  components: {
    ProductList,
    ShoppingCart,
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

<style>
#app {
  background-color: #202123;
  color: white;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-family: Arial, sans-serif;
  text-align: center;
}

.container {
  display: flex;
  justify-content: space-between;
  width: 60%;
}

h1 {
  margin-bottom: 20px;
}
</style>
