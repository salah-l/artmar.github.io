<!-- Footer.vue -->
<template>
  <!--==================== FOOTER ====================-->
  <footer class="footer section">
    <div class="footer__container container grid">
      <div class="footer__content">
        <h3 class="footer__title">Our information</h3>

        <ul class="footer__list">
          <li>Rabat</li>
          <li>Madinat ALIRFANE</li>
          <li>123-456-789</li>
        </ul>
      </div>
      <div class="footer__content">
        <h3 class="footer__title">About Us</h3>

        <ul class="footer__links">
          <li>
            <a href="#" class="footer__link">Customer Support</a>
          </li>
          <li>
            <a href="#" class="footer__link">About Us</a>
          </li>
          <li>
            <a href="#" class="footer__link">Copy Right</a>
          </li>
        </ul>
      </div>

      <div class="footer__content">
        <h3 class="footer__title">Social</h3>

        <ul class="footer__social">
          <a href="https://www.facebook.com/" target="_blank" class="footer__social-link">
            <i class="bx bxl-facebook"></i>
          </a>

          <a href="https://twitter.com/" target="_blank" class="footer__social-link">
            <i class="bx bxl-twitter"></i>
          </a>

          <a href="https://www.instagram.com/" target="_blank" class="footer__social-link">
            <i class="bx bxl-instagram"></i>
          </a>
        </ul>
      </div>
    </div>

    <span class="footer__copy">&#169; Artmar. All rigths reserved</span>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
  // Your component's script section
}
</script>

<style scoped>
/* Your header CSS goes here */
</style>
