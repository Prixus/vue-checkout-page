<template>
  <fragment>
    <navigation-bar :a-cart="aCart"></navigation-bar>
    <b-container>
      <checkout-box @add-to-cart="handleAddToCart"></checkout-box>
    </b-container>
  </fragment>
</template>

<script>

import CheckoutBox from '../components/CheckoutBox/CheckoutBox';
import NavigationBar from '../components/NavigationBar/NavigationBar';

/**
 * App Component
 * @author Simon Peter Calamno
 * @since 2022.06.01
 */
export default {
  name: 'App',
  components: {NavigationBar, CheckoutBox},
  data() {
    return {
        aCart : []
    }
  },
  methods: {
    /**
     * Appends the added cart item at the beginning of the list
     * @param oCartItem
     */
    handleAddToCart(oCartItem) {
      this.aCart.unshift(oCartItem);
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.row-no-padding [class*="col-"] {
  padding-left: 0 !important;
  padding-right: 0 !important;
}

.no-padding {
  padding-left: 0 !important;
  padding-right: 0 !important;
}
</style>
