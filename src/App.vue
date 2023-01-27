<template>
  <main id="product-catalog">
    <div class="product-catalog-header">
      <h1>Каталог</h1>
      <select v-model="selectedCategory" @change="filterByCategory">
        <option value="">Все товары</option>
        <option v-for="category in categories" :value="category.name">{{ category.name }}</option>
      </select>
    </div>
    <div class="products">
      <ProductCard v-for="product in filteredProducts" :key="product.id" :product="product"/>
    </div>
  </main>
</template>

<script>
import ProductCard from './components/ProductCard.vue'

export default {
  components: {
    ProductCard
  },
  data() {
    return { 
      selectedCategory: '',
      products: [],
      categories: [],
       cart: []
    }
  },
  created() {
    fetch('./products.json')
      .then(response => response.json())
      .then(data => {
        this.products = data.products
        this.categories = data.categories
      })
  },
  computed: {
    filteredProducts() {
      if (!this.selectedCategory) {
        return this.products
      }
      return this.products.filter(product => product.product_type === this.selectedCategory)
    }
  },
}
</script>
<style>
  #product-catalog h1 {
    margin: 15px;
  }
  .product-catalog-header {
    display: flex;
    align-items: center;
  }
  .product-catalog-header select {
    height: 32px;
  }
  .products {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  @media (max-width: 600px) {
    .product-catalog-header {
      display: block;
    }
    .product-catalog-header select {
      margin: 1rem;
      margin-top: 0;
    }
  }
</style>
