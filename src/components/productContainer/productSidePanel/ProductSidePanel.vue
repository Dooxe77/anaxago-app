<template>
  <div class="product-side-panel">
    <Product-status />
    <Panel>
      <Product-actions />
    </Panel>
  </div>
</template>

<script>
import Panel from '../../shared/Panel';
import ProductActions from './productActions/ProductActions';
import ProductStatus from './productStatus/ProductStatus';

export default {
  name: 'ProductSidePanel',
  components: {
    Panel,
    ProductActions,
    ProductStatus
  }
}
</script>

<style lang="scss">
  @import "../../../styles/variables.scss";

  .product-side-panel {
    height: 100%;
    display: flex;
    flex-direction: column;
  }
</style>
