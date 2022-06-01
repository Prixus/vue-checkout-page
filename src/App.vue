<template>
  <div>
    <checkout-box></checkout-box>
  </div>
</template>

<script>
  import CheckoutBox from "./components/CheckoutBox/CheckoutBox.vue";

  /**
   * App Component
   *
   * @author Simon Peter Calamno
   * @since 2022.06.01
   */
  export default {
    name: 'App',
    components: {CheckoutBox},
    data() {
      return {
        greeting: 'Hello World!'
      }
    }
  }
</script>

<style lang="scss">
@import "~@/assets/scss/vendors/bootstrap-vue/index";
@import './assets/base.css';
</style>
