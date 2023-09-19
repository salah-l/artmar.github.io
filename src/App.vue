<!-- App.vue -->
<template>
  <Header :cart-items-count="cartItemsCount" />
  <Cart @cart-update="updateCart" :cart="cart" />
  <MainContent @add-to-cart="addToCart" />
  <Footer />
  <!--=============== Added To Cart Message ===============-->
  <transition name="slide-fade">
    <div
      v-if="showMessage"
      class="fixed p-4 flex gap-2 items-center bottom-4 left-4 w-[300px] h-[80px] bg-[#e5c048] shadow transition-transform transition-opacity"
    >
      <i class="bx bxs-check-circle text-white"></i>

      <div class="added-tocart-message text-white font-bold">
        <span> {{ product }} added to cart!</span>
      </div>
    </div>
  </transition>
  <!--=============== SCROLL UP ===============-->
  <a href="#" class="scrollup" id="scroll-up" ref="scrollUp">
    <i class="bx bx-up-arrow-alt scrollup__icon"></i>
  </a>
</template>

<script>
import Header from './components/HeaderComponenet.vue'
import Cart from './components/cart/Cart.vue'
import MainContent from './components/MainContent.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    Cart,
    MainContent,
    Footer
  },
  data() {
    return {
      cart: [],
      cartItemsCount: 0,
      product: 'test',
      showMessage: false
    }
  },
  methods: {
    addToCart(product) {
      let existingProduct = this.cart.find((item) => item.id === product.id)

      if (existingProduct) {
        existingProduct.quantity += 1
      } else {
        let cartItem = { ...product, quantity: 1 }
        this.cart.push(cartItem)
      }

      this.product = product.name
      this.cartItemsCount = this.getCaretTotalItems()
      this.showCartMessage()
    },
    updateCart(newCart) {
      this.cart = newCart
      this.cartItemsCount = this.getCaretTotalItems()
    },
    getCaretTotalItems() {
      return this.cart.reduce((sum, product) => {
        return sum + product.quantity
      }, 0)
    },
    showCartMessage() {
      this.showMessage = true
      setTimeout(() => {
        this.showMessage = false
      }, 1000)
    }
  },
  mounted() {
    /*=============== SHOW MENU ===============*/
    const navMenu = document.getElementById('nav-menu'),
      navToggle = document.getElementById('nav-toggle'),
      navClose = document.getElementById('nav-close')

    /*===== MENU SHOW =====*/
    /* Validate if constant exists */
    if (navToggle) {
      navToggle.addEventListener('click', () => {
        navMenu.classList.add('show-menu')
      })
    }

    /*===== MENU HIDDEN =====*/
    /* Validate if constant exists */
    if (navClose) {
      navClose.addEventListener('click', () => {
        navMenu.classList.remove('show-menu')
      })
    }

    /*=============== REMOVE MENU MOBILE ===============*/
    const navLink = document.querySelectorAll('.nav__link')

    const linkAction = () => {
      const navMenu = document.getElementById('nav-menu')
      // When we click on each nav__link, we remove the show-menu class
      navMenu.classList.remove('show-menu')
    }
    navLink.forEach((n) => n.addEventListener('click', linkAction))

    /*=============== TESTIMONIAL SWIPER ===============*/
    let testimonialSwiper = new Swiper('.testimonial-swiper', {
      spaceBetween: 30,
      loop: 'true',

      navigation: {
        nextEl: '.swiper-button-next',
        prevEl: '.swiper-button-prev'
      }
    })

    /*=============== NEW SWIPER ===============*/
    let newSwiper = new Swiper('.new-swiper', {
      spaceBetween: 24,
      loop: 'true',

      breakpoints: {
        576: {
          slidesPerView: 2
        },
        768: {
          slidesPerView: 3
        },
        1024: {
          slidesPerView: 4
        }
      }
    })

    /*=============== SCROLL SECTIONS ACTIVE LINK ===============*/
    const sections = document.querySelectorAll('section[id]')

    const scrollActive = () => {
      const scrollDown = window.scrollY

      sections.forEach((current) => {
        const sectionHeight = current.offsetHeight,
          sectionTop = current.offsetTop - 58,
          sectionId = current.getAttribute('id'),
          sectionsClass = document.querySelector('.nav__menu a[href*=' + sectionId + ']')

        if (scrollDown > sectionTop && scrollDown <= sectionTop + sectionHeight) {
          sectionsClass.classList.add('active-link')
        } else {
          sectionsClass.classList.remove('active-link')
        }
      })
    }
    window.addEventListener('scroll', scrollActive)

    /*=============== SHOW SCROLL UP ===============*/

    let appInstance = this
    window.addEventListener('scroll', function () {
      let scrollUp = appInstance.$refs.scrollUp

      this.scrollY >= 350
        ? scrollUp.classList.add('show-scroll')
        : scrollUp.classList.remove('show-scroll')
    })
  }
}
</script>

<style>
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition:
    opacity 1s,
    transform 1s;
}
.slide-fade-enter,
.slide-fade-leave-to {
  opacity: 0;
  transform: translateY(100%);
}
</style>
