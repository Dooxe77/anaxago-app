<template>
  <div class="home">
    <Product-container />
  </div>
</template>

<script>
import ProductContainer from '../productContainer/ProductContainer';

export default {
  name: 'Home',
  components: {
    ProductContainer,
  },
  data() {
    return {

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
