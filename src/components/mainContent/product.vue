<!-- Product.vue -->
<template>
  <article class="products__card min-h-[250px]">
    <img :src="`/img/products/product${product.img.id}.png`" alt="" class="products__img mx-auto" />

    <h3 class="products__title mt-[-10px]">{{ product.name }}</h3>
    <span class="products__price mt-[-10px]"
      >{{ product.price.value }} {{ product.price.currency }}</span
    >

    <button class="products__button" @mousedown="addToCart">
      <span class="text-sm"> Add to </span>
      <i class="bx bx-shopping-bag"></i>
    </button>
  </article>
</template>

<script>
export default {
  name: 'Product',
  props: {
    product: Object
  },
  methods: {
    addToCart() {
      this.$emit('addToCart', this.product)
    }
  }
}
</script>

<style scoped>
/* Your header CSS goes here */
</style>
