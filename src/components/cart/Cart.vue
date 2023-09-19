<!-- Cart.vue -->
<template>
  <!--==================== CART ====================-->
  <div class="cart" id="cart">
    <i class="bx bx-x cart__close" id="cart-close"></i>

    <h2 class="cart__title-center">My Cart</h2>

    <div v-if="newCart.length" class="cart__container h-2/3 overflow-auto">
      <CartProduct
        :key="product.id"
        @update-product="updateCart"
        @remove-from-cart="removeFromCart"
        v-for="product in newCart"
        :product="product"
      />
    </div>

    <div v-if="newCart.length" class="cart__prices mb-2">
      <span class="cart__prices-item">{{ cartMetadata.numberOfItems }} items</span>
      <span class="cart__prices-total">{{ cartMetadata.amount }} {{ cartMetadata.currency }}</span>
    </div>

    <button
      v-if="newCart.length"
      class="checkout w-full h-[40px] bg-[#e5c048] text-white font-bold text-md"
    >
      Checkout
    </button>

    <div v-if="!newCart.length" class="w-full h-1/2 flex flex-col items-center justify-center">
      <div class="empty-cart-mascot"></div>
      <div>
        <span class="empty-cart-text text-lg text-gray-400">It's empty in here...</span>
      </div>
    </div>
  </div>
</template>

<script>
import CartProduct from './cartProduct.vue'
export default {
  name: 'Cart',
  components: { CartProduct },
  props: {
    cart: Array
  },
  data() {
    return {
      newCart: [],
      cartMetadata: {
        currency: 'MAD',
        amount: 0,
        numberOfItemTypes: 0,
        numberOfItems: 0
      }
    }
  },
  methods: {
    getProductById(id) {
      return products.find((product) => product.id === id)
    },
    getCartTotalAmount() {
      return this.newCart.reduce((sum, product) => {
        return sum + product.price.value * product.quantity
      }, 0)
    },
    getCaretTotalItems() {
      return this.newCart.reduce((sum, product) => {
        return sum + product.quantity
      }, 0)
    },
    removeProductById(id) {
      return this.newCart.filter((product) => product.id !== id)
    },
    updateCart(newProductDetails) {
      if (!newProductDetails) {
        return
      }

      const currentProductDetails = this.newCart.find(
        (product) => product.id === newProductDetails.id
      )

      if (currentProductDetails) {
        Object.assign(currentProductDetails, newProductDetails)
        this.cartMetadata.amount = this.getCartTotalAmount()
        this.cartMetadata.numberOfItems = this.getCaretTotalItems()
        this.$emit('cartUpdate', this.newCart)
      } else {
        console.warn(`Product with ID ${id} not found`)
      }
    },
    removeFromCart(productToDelete) {
      this.newCart = this.removeProductById(productToDelete.id)
      this.cartMetadata.amount = this.getCartTotalAmount()
      this.cartMetadata.numberOfItems = this.getCaretTotalItems()
      this.$emit('cartUpdate', this.newCart)
    }
  },
  mounted() {
    this.newCart = this.cart
    this.cartMetadata = {
      currency: 'MAD',
      amount: 0,
      numberOfItemTypes: 0,
      numberOfItems: 0
    }

    this.cartMetadata.amount = this.getCartTotalAmount()
    this.cartMetadata.numberOfItemTypes = this.newCart.length
    this.cartMetadata.numberOfItems = this.getCaretTotalItems()
  },

  watch: {
    cart: {
      handler(newVal, oldVal) {
        this.newCart = newVal
        this.cartMetadata.amount = this.getCartTotalAmount()
        this.cartMetadata.numberOfItemTypes = this.newCart.length
        this.cartMetadata.numberOfItems = this.getCaretTotalItems()
      },
      deep: true
    }
  }
}
</script>

<style scoped>
.empty-cart-mascot {
  width: 140px;
  height: 140px;
  background-image: url('img/meta/empty-cart.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
</style>
