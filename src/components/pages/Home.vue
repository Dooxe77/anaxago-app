<template>
  <div class="home">
    <Product-container :product="product"/>
    <Product-investment-forms />
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
    };
  },
}
</script>

<style lang="scss">
  .home {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>
