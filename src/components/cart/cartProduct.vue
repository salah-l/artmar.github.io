<!-- cartProduct.vue -->
<template>
  <article class="cart__card" ref="article">
    <div class="cart__box">
      <img :src="`img/products/product${product.img.id}.png`" alt="" class="cart__img" />
    </div>

    <div class="cart__details">
      <h3 class="cart__title">{{ product.name }}</h3>
      <span class="cart__price">{{ product.price.value }} {{ product.price.currency }}</span>

      <div class="cart__amount">
        <div class="cart__amount-content">
          <span
            class="cart__amount-box"
            ref="sub"
            @mousedown="startSubtracting"
            @mouseup="stopSubtracting"
            @mouseleave="stopSubtracting"
          >
            <i class="bx bx-minus"></i>
          </span>

          <span class="cart__amount-number">{{ product.quantity }}</span>

          <span
            class="cart__amount-box"
            ref="add"
            @mousedown="startAdding"
            @mouseup="stopAdding"
            @mouseleave="stopAdding"
          >
            <i class="bx bx-plus"></i>
          </span>
        </div>

        <i class="bx bx-trash-alt cart__amount-trash" @click="deleteArticle"></i>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  name: 'CartProduct',
  props: {
    product: Object
  },
  data() {
    return {
      interval: null
    }
  },

  methods: {
    startAdding() {
      this.add()
      this.interval = setInterval(this.add, 100)
    },
    stopAdding() {
      clearInterval(this.interval)
    },
    add() {
      if (this.product.quantity < 99) {
        this.product.quantity += 1
        this.$emit('updateProduct', this.product)
      }
    },
    startSubtracting() {
      this.sub()
      this.interval = setInterval(this.sub, 100)
    },
    stopSubtracting() {
      clearInterval(this.interval)
    },
    sub() {
      if (this.product.quantity > 1) {
        this.product.quantity -= 1
        this.$emit('updateProduct', this.product)
      }
    },
    deleteArticle() {
      console.log('Removed')
      this.$refs.article.remove()
      this.$emit('removeFromCart', this.product)
    }
  }
}
</script>

<style scoped>
/* Your header CSS goes here */
</style>
