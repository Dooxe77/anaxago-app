<template>
  <div class="product-container">
    <product-infos :product-infos="productInfos" class="product-infos-content"/>
    <Panel class="product-side-panel-content">
      <product-side-panel :product-status="productStatus"/>
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
  },
  props: {
    product: {
      type: Object,
      required: true,
    }
  },
  computed: {
    productInfos() {
      return {
        "name": this.product.name,
        "description": this.product.description,
        "type": this.product.type,
        "distribution": this.product.distribution,
        "horizon": this.product.horizon,
        "emittedInstrument": this.product.emittedInstrument,
        "imgUrl": this.product.imgUrl,
      }
    },
    productStatus() {
      return {
        "targetAmount": this.product.targetAmount,
        "currentAmount": this.product.currentAmount,
      }
    },
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
