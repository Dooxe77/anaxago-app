<template>
  <div class="home">
    <Product-container :product="product"/>
  </div>
</template>

<script>
import ProductContainer from '../productContainer/ProductContainer';
import productMock from '../../productMock.json';

export default {
  name: 'Home',
  components: {
    ProductContainer,
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
    justify-content: center;
  }
</style>
