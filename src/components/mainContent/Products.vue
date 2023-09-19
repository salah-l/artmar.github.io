<!-- Products.vue -->
<template>
  <!--==================== PRODUCTS ====================-->
  <section class="products section container" id="products">
    <h2 class="section__title">Products</h2>

    <div class="products__container grid">
      <Product @add-to-cart="addToCart" v-for="product in products" :product="product" />
    </div>
  </section>
</template>

<script>
import Product from './Product.vue'
export default {
  name: 'Products',
  components: { Product },
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
        id: 1,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 1,
          alt: 'Product 1'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
      {
        id: 2,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 2,
          alt: 'Product 2'
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
        id: 4,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 4,
          alt: 'Product 4'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
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
        id: 6,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 6,
          alt: 'Product 6'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
      {
        id: 7,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 7,
          alt: 'Product 7'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
      {
        id: 8,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 8,
          alt: 'Product 8'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
      {
        id: 9,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 9,
          alt: 'Product 9'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
      {
        id: 10,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 10,
          alt: 'Product 10'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
      {
        id: 11,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 11,
          alt: 'Product 11'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
      {
        id: 12,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 12,
          alt: 'Product 12'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
      {
        id: 13,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 13,
          alt: 'Product 13'
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
      },
      {
        id: 15,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 15,
          alt: 'Product 15'
        },
        name: 'White Sac',
        price: {
          value: 79,
          currency: 'MAD'
        }
      },
      {
        id: 16,
        feature: {
          isFeatured: false,
          caption: 'Sale'
        },
        img: {
          id: 16,
          alt: 'Product 16'
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
