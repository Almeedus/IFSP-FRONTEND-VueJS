<template>
    <div>
      <h2>Seu Carrinho</h2>
      <div v-if="cart.length > 0">
        <div v-for="item in cart" :key="item.id" class="cart-item">
          <p>{{ item.name }} - {{ item.quantity }} x {{ item.price | currency }}</p>
          <button @click="$emit('remove-from-cart', item.id)">Remover</button>
        </div>
        <p>Total: {{ cartTotal | currency }}</p>
      </div>
      <div v-else>
        <p>Seu carrinho está vazio.</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      cart: Array,
    },
    computed: {
      cartTotal() {
        return this.cart.reduce((total, item) => total + item.price * item.quantity, 0);
      },
    },
    filters: {
      currency(value) {
        return 'R$ ' + value.toFixed(2);
      },
    },
  };
  </script>
  
  <style>
  .shopping-cart {
    flex: 1;
    padding: 20px;
  }
  
  .cart-item {
    margin-bottom: 10px;
  }
  
  button {
    background-color: #ff4d4f;
    color: white;
    border: none;
    padding: 5px 10px;
    cursor: pointer;
    border-radius: 4px;
  }
  
  button:hover {
    background-color: #ff7875;
  }
  </style>