<!-- FeaturedProduct.vue -->
<template>
  <article class="featured__card">
    <span class="featured__tag">{{ featuredProduct.feature.caption }}</span>

    <img
      :src="`img/products/product${featuredProduct.img.id}.png`"
      alt=""
      class="featured__img mx-auto"
    />

    <div class="featured__data">
      <h3 class="featured__title">{{ featuredProduct.name }}</h3>
      <span class="featured__price"
        >{{ featuredProduct.price.value }} {{ featuredProduct.price.currency }}</span
      >
    </div>

    <button class="button featured__button" @mousedown="addToCart">{{ callToAction }}</button>
  </article>
</template>

<script>
export default {
  name: 'FeatureProduct',
  props: {
    featuredProduct: Object
  },
  data() {
    return {
      callToAction: 'ADD TO CART'
    }
  },
  methods: {
    addToCart() {
      this.$emit('addToCart', this.featuredProduct)
    }
  }
}
</script>

<style scoped>
/* Your header CSS goes here */
</style>
