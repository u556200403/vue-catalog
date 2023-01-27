<template>
    <div class="product-card">
      <div class="product-type">
        <p>{{ product.product_type }} </p>
      </div>
      <div class="product-image">
        <img :src="product.image_link" :alt="product.title">
      </div>
      <div class="product-info">
       
        <h3>{{ product.title }}</h3>
        <div class="product-price">
          <p>{{ product.price }}</p>
        </div>
        <button class="buy-button" @click="addToCart">Добавить в корзину</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      product: {
        type: Object,
        required: true
      }
    },
    methods: {
      addToCart() {
        this.$emit('add-to-cart', this.product);
      }
    }
  }
  </script>
<style>
  .product-card {
    padding: 1.6%;
    flex-basis: 16%;
    box-shadow: rgb(99 99 99 / 20%) 0px 2px 8px 0px;
    border-radius: 16px;
    margin: 0.3%;
    display: flex;
    flex-direction: column;
    justify-content: stretch;
  }
  .product-type {
    text-align: center;
    margin: 0.4rem;
  }
  .product-image {
    width: 100%;
    margin-bottom: 0.4rem;
  }
  .product-image img {
    max-width: 100%;
  }
  .product-info {
    margin-top: auto;
    display: flex;
    flex-direction: column;
    min-height: 6.5rem;
    justify-content: space-between;
  }
  .product-info h3 { 
    margin: 0 auto;
  }
  .product-price {
    text-align: center;
    font-weight: 500;
  }
  .buy-button {
    font-weight: 500;
    background: #fe5000;
    color: #fff;
    margin: 0;
    height: 2rem;
    border-radius: 15px;
    border: none;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: 0.3s;
    border-radius: 3px;
    padding: 0;
    cursor: pointer;
  }
  .buy-button:hover {
    box-shadow: 0 12px 18px -11px rgb(254 80 0 / 69%);
    transition: 0.3s;
  }
  @media (max-width: 920px) {
    .product-card {
      flex: 1 21%;
    }
  }
  @media (max-width: 600px) {
    .product-card {
      flex: 1 46%;
      padding: 1%;
      margin: 1%;
    }
  }
  @media (max-width: 450px) {
    .product-card {
      flex: 1 100%;
      padding: 1%;
      margin: 1%;
    }
  }
</style>