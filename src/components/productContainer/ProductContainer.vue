<template>
  <div class="product-container">
    <Panel class="product-infos-content">
      <product-infos />
    </Panel>
    <Panel class="product-side-panel-content">
      <product-side-panel />
    </Panel>
  </div>
</template>

<script>
import Panel from '../shared/Panel';
import ProductInfos from './productInfos/ProductInfos';
import ProductSidePanel from './productSidePanel/ProductSidePanel';

export default {
  name: 'ProductContainer',
  components: {
    Panel,
    ProductInfos,
    ProductSidePanel,
  }
}
</script>

<style lang="scss">
@import "../../styles/variables.scss";

  .product-container {
    // TEMP
    min-height: 600px;

    max-width: 1080px;
    margin-top: 50px;
    display: flex;
    flex: 1;

    .product-infos-content{
      flex: 3;
      margin-right: $spacing-lg;
    }

    .product-side-panel-content {
      flex: 1;
    }
  }
</style>
