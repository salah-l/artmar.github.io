<!-- Header.vue -->
<template>
  <header class="header" id="header" ref="header">
    <nav class="nav container">
      <a href="#" class="nav__logo">
        <!-- <i class="bx bxs-watch nav__logo-icon"></i> Rolex -->
        <img src="/img/meta/logo.png" alt="" class="logo_artmar" />
      </a>

      <div class="nav__menu z-[9999]" id="nav-menu">
        <ul class="nav__list">
          <li class="nav__item">
            <a href="#home" class="nav__link active-link">Home</a>
          </li>
          <li class="nav__item">
            <a href="#featured" class="nav__link">Featured</a>
          </li>
          <li class="nav__item">
            <a href="#products" class="nav__link">Products</a>
          </li>
          <li class="nav__item">
            <a href="#new" class="nav__link">Contact</a>
          </li>
        </ul>

        <div class="nav__close" id="nav-close">
          <i class="bx bx-x"></i>
        </div>
      </div>

      <div class="nav__btns">
        <!-- Theme change button -->
        <i class="bx bx-moon change-theme" id="theme-button" ref="theme"></i>

        <div class="nav__shop relative" id="cart-shop" ref="cart">
          <i class="bx bx-shopping-bag"></i>
          <div
            v-show="cartItemsCount"
            ref="notif"
            class="absolute w-[16px] h-[16px] rounded-[100px] right-[-6px] bottom-0 text-[0.7rem] font-bold flex items-center justify-center"
          >
            {{ cartItemsCount }}
          </div>
        </div>

        <div class="nav__toggle" id="nav-toggle">
          <i class="bx bx-grid-alt" ref="menu"></i>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
import '../../public/js/swiper-bundle.min.js'
export default {
  name: 'Header',
  props: {
    cartItemsCount: Number
  },
  mounted() {
    const headerInstance = this
    const header = this.$refs.header

    const themeButton = this.$refs.theme
    const cartButton = this.$refs.cart
    const mobileMenu = this.$refs.menu
    const notif = this.$refs.notif

    themeButton.style.color = 'rgb(255, 255, 255)'
    themeButton.style.mixBlendMode = 'difference'
    cartButton.style.color = 'rgb(255, 255, 255)'
    cartButton.style.mixBlendMode = 'difference'
    notif.style.color = 'white'
    notif.style.background = 'red'
    mobileMenu.style.color = 'rgb(255, 255, 255)'
    mobileMenu.style.mixBlendMode = 'difference'

    /*=============== CHANGE BACKGROUND HEADER ===============*/
    window.addEventListener('scroll', function () {
      // When the scroll is greater than 50 viewport height, add the scroll-header class to the header tag

      let currentselectedTheme = localStorage.getItem('selected-theme')
      console.log(currentselectedTheme)

      if (currentselectedTheme === 'light') {
        if (this.scrollY >= 50) {
          header.classList.add('scroll-header')

          setTimeout(() => {
            notif.style.color = 'black'
            notif.style.background = 'cyan'
          }, 100)
        } else {
          header.classList.remove('scroll-header')
          setTimeout(() => {
            notif.style.color = 'white'
            notif.style.background = 'red'
          }, 100)
        }
      } else {
        if (this.scrollY >= 50) {
          header.classList.add('scroll-header')

          setTimeout(() => {
            notif.style.color = 'white'
            notif.style.background = 'red'
          }, 100)
        } else {
          header.classList.remove('scroll-header')
          setTimeout(() => {
            notif.style.color = 'white'
            notif.style.background = 'red'
          }, 100)
        }
      }
    })

    /*=============== SHOW CART ===============*/
    const cart = document.getElementById('cart'),
      cartShop = document.getElementById('cart-shop'),
      cartClose = document.getElementById('cart-close')

    /*===== CART SHOW =====*/
    /* Validate if constant exists */
    if (cartShop) {
      cartShop.addEventListener('click', () => {
        cart.classList.add('show-cart')
      })
    }

    /*===== CART HIDDEN =====*/
    /* Validate if constant exists */
    if (cartClose) {
      cartClose.addEventListener('click', () => {
        cart.classList.remove('show-cart')
      })
    }

    /*=============== DARK LIGHT THEME ===============*/
    const darkTheme = 'dark-theme'
    const iconTheme = 'bx-sun'

    // Previously selected topic (if user selected)
    const selectedTheme = localStorage.getItem('selected-theme')
    const selectedIcon = localStorage.getItem('selected-icon')

    // We obtain the current theme that the interface has by validating the dark-theme class
    const getCurrentTheme = () => (document.body.classList.contains(darkTheme) ? 'dark' : 'light')
    const getCurrentIcon = () =>
      themeButton.classList.contains(iconTheme) ? 'bx bx-moon' : 'bx bx-sun'

    // We validate if the user previously chose a topic
    if (selectedTheme) {
      // If the validation is fulfilled, we ask what the issue was to know if we activated or deactivated the dark
      document.body.classList[selectedTheme === 'dark' ? 'add' : 'remove'](darkTheme)
      themeButton.classList[selectedIcon === 'bx bx-moon' ? 'add' : 'remove'](iconTheme)
    }

    // Activate / deactivate the theme manually with the button
    themeButton.addEventListener('click', () => {
      // Add or remove the dark / icon theme
      document.body.classList.toggle(darkTheme)
      themeButton.classList.toggle(iconTheme)

      // We save the theme and the current icon that the user chose
      localStorage.setItem('selected-theme', getCurrentTheme())
      localStorage.setItem('selected-icon', getCurrentIcon())

      let currentselectedTheme = localStorage.getItem('selected-theme')
      console.log(currentselectedTheme)
      if (currentselectedTheme === 'light') {
        if (window.scrollY >= 50) {
          console.log('1')
          setTimeout(() => {
            notif.style.color = 'black'
            notif.style.background = 'cyan'
          }, 100)
        } else {
          console.log('2')
          setTimeout(() => {
            notif.style.color = 'white'
            notif.style.background = 'red'
          }, 100)
        }
      } else {
        if (window.scrollY >= 50) {
          console.log('3')
          setTimeout(() => {
            notif.style.color = 'white'
            notif.style.background = 'red'
          }, 100)
        } else {
          console.log('4')
          setTimeout(() => {
            notif.style.color = 'white'
            notif.style.background = 'red'
          }, 100)
        }
      }
    })
  }
}
</script>

<style scoped>
/* Your header CSS goes here */
</style>
