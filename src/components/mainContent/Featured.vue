<!-- Featured.vue -->
<template>
  <!--==================== FEATURED ====================-->
  <section class="featured section container" id="featured">
    <h2 class="section__title">Featured</h2>

    <div class="featured__container grid">
      <featuredProduct
        @add-to-cart="addToCart"
        v-for="product in products"
        :featured-product="product"
      />
    </div>
  </section>
</template>

<script>
import featuredProduct from './featuredProduct.vue'
export default {
  name: 'Featured',
  components: { featuredProduct },
  props: {
    featuredProducts: Array
  },
  data() {
    return {
      products: []
    }
  },
  methods: {
    addToCart(product) {
      this.$emit('addToCart', product)
    }
  },
  created() {
    this.products = [
      {
        id: 5,
        feature: {
          isFeatured: true,
          caption: 'Sale'
        },
        img: {
          id: 5,
          alt: 'Product 5'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
      {
        id: 3,
        feature: {
          isFeatured: true,
          caption: 'Sale'
        },
        img: {
          id: 3,
          alt: 'Product 3'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
      {
        id: 14,
        feature: {
          isFeatured: true,
          caption: 'New'
        },
        img: {
          id: 14,
          alt: 'Product 14'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      }
    ]
  }
}
</script>

<style scoped>
/* Your header CSS goes here */
</style>
