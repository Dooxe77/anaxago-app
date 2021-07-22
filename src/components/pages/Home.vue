<template>
  <div class="home">
    <Product-container :product="product" @open-product-forms="openProductForms"/>
    <Product-investment-forms v-if="isOpenProductForm" @close-product-forms="closeProductForms"/>
  </div>
</template>

<script>
import ProductContainer from '../productContainer/ProductContainer';
import ProductInvestmentForms from '../productInvestmentForms/ProductInvestmentForms';

import productMock from '../../productMock.json';

export default {
  name: 'Home',
  components: {
    ProductContainer,
    ProductInvestmentForms,
  },
  data() {
    return {
      product: productMock,
      isOpenProductForm: false,
    };
  },
  methods: {
    openProductForms() {
      this.isOpenProductForm = true;
    },
    closeProductForms() {
      this.isOpenProductForm = false;
    },
  }
}
</script>

<style lang="scss">
  .home {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 50px 0;
  }
</style>
