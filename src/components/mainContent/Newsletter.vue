<!-- Newsletter.vue -->
<template>
  <!--==================== NEWSLETTER ====================-->
  <section class="newsletter section container">
    <div class="newsletter__bg grid">
      <div>
        <h2 class="newsletter__title">
          Subscribe To Our <br />
          Newsletter!
        </h2>
        <p class="newsletter__description">
          Don't miss out on your discounts. Subscribe to our email newsletter to get the best
          offers, discounts, coupons, gifts and much more.
        </p>
      </div>

      <form action="" class="newsletter__subscribe">
        <input type="email" placeholder="Enter your email" class="newsletter__input" />
        <button class="button">SUBSCRIBE</button>
      </form>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Newsletter'
  // Your component's script section
}
</script>

<style scoped>
/* Your header CSS goes here */
</style>
