<!-- MainContent.vue -->
<template>
  <main class="main">
    <Home />
    <Featured @add-to-cart="addToCart" />
    <Products @add-to-cart="addToCart" />
    <NewArrivals />
    <Newsletter />
  </main>
</template>

<script>
import Home from './mainContent/Home.vue'
import Featured from './mainContent/Featured.vue'
import Products from './mainContent/Products.vue'
import Newsletter from './mainContent/Newsletter.vue'

export default {
  name: 'MainContent',
  components: {
    Home,
    Featured,
    Products,
    Newsletter
  },
  methods: {
    addToCart(product) {
      this.$emit('addToCart', product)
    }
  }
}
</script>

<style scoped>
/* Your main content CSS goes here */
</style>
