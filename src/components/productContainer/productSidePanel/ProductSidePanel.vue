<template>
  <div class="product-side-panel">
    <Panel class="product-status-panel">
      <Product-status :product-status="productStatus"/>
    </Panel>
    <Panel class="product-actions-panel">
      <Product-actions />
    </Panel>
    <Panel class="product-contact-panel">
      <Contact-infos :product-contact="productContact"/>
    </Panel>
  </div>
</template>

<script>
import Panel from "../../shared/Panel";
import ProductStatus from './productStatus/ProductStatus';
import ContactInfos from "./contactInfos/ContactInfos";
import ProductActions from "./productActions/ProductActions";

export default {
  name: 'ProductSidePanel',
  components: {
    ContactInfos,
    Panel,
    ProductActions,
    ProductStatus
  }, 
  props: {
    productStatus: {
      type: Object,
      required: true,
    },
     productContact: {
      type: Object,
      required: true,
    }
  },
}
</script>

<style lang="scss">
  @import "../../../styles/variables.scss";

  .product-side-panel {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;

    .product-status-panel {
      margin-bottom: 30px;
    }

    .product-actions-panel {
      margin-bottom: 30px;
    }
  }
</style>
