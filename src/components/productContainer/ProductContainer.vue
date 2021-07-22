<template>
  <div class="product-container">
    <Product-infos :product-infos="productInfos" class="product-infos-content"/>
    <Product-side-panel 
      :product-status="productStatus" 
      :product-contact="productContact"
      class="product-side-panel-content"/>
  </div>
</template>

<script>
import ProductInfos from './productInfos/ProductInfos';
import ProductSidePanel from './productSidePanel/ProductSidePanel';

export default {
  name: 'ProductContainer',
  components: {
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
    productContact() {
      return this.product.contactInfos;
    },
  }
}
</script>

<style lang="scss">
@import "../../styles/variables.scss";

  .product-container {
    min-height: 600px;
    max-width: 1080px;
    margin: 50px 0;
    display: flex;
    flex: 1;

    @media (max-width: $tablet-breakpoint) {
      flex-direction: column;
      margin: 50px;
    }

    .product-infos-content{
      flex: 3;

      @media (min-width: $tablet-breakpoint) {
        margin-right: $spacing-lg;
      }
    }

    .product-side-panel-content {
      flex: 1;
    }
  }
</style>
