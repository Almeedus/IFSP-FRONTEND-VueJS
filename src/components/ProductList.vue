<template>
    <div>
      <h2>Produtos Disponíveis</h2>
      <div v-for="product in products" :key="product.id" class="product">
        <p>{{ product.name }} - {{ product.price | currency }}</p>
        <button @click="$emit('add-to-cart', product)">Adicionar ao Carrinho</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        products: [
          { id: 1, name: 'Produto A', price: 100 },
          { id: 2, name: 'Produto B', price: 150 },
        ],
      };
    },
    filters: {
      currency(value) {
        return 'R$ ' + value.toFixed(2);
      },
    },
  };
  </script>
  
  <style>
  .product {
    margin-bottom: 10px;
  }
  </style>
  