<!-- Home.vue -->
<template>
  <section class="home" id="home">
    <div class="home__container container grid">
      <div class="home__img-bg">
        <img src="img/meta/home.jpg" alt="" class="home__img" />
      </div>

      <!-- <div class="home__social">
        <a href="https://www.facebook.com/" target="_blank" class="home__social-link"> Facebook </a>
        <a href="https://twitter.com/" target="_blank" class="home__social-link"> Twitter </a>
        <a href="https://www.instagram.com/" target="_blank" class="home__social-link">
          Instagram
        </a>
      </div> -->

      <div class="home__data">
        <h1 class="home__title">
          THE BEST ARTSHOP<br />
          IN THE WORLD
        </h1>
        <p class="home__description">
          Art products made with creativity, inspiration and above all, love.
        </p>
        <span class="home__price">Check out our products now!</span>

        <div class="home__btns">
          <a href="#products" class="button button--gray button--small"> Browse </a>

          <!-- <button class="button home__button">ADD TO CART</button> -->
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Home'
  // Your component's script section
}
</script>

<style scoped>
/* Your header CSS goes here */
</style>
