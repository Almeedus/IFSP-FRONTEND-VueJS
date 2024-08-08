<template>
    <div class="product-list">
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
          { id: 1, name: 'Caneta', price: 1.30 },
          { id: 2, name: 'Corretivo', price: 8.99 },
          { id: 3, name: 'Lápis', price: 1.23 },
          { id: 4, name: 'Borracha', price: 8.23 },
          { id: 5, name: 'Régua', price: 18.35 },
          { id: 6, name: 'Caderno', price: 38.87 },
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
  .product-list {
    flex: 1;
    padding: 20px;
    text-align: right;
  }
  
  .product {
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
  