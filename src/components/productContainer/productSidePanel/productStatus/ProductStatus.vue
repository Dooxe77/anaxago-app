<template>
  <div class="product-status">
    Product status
  </div>
</template>

<script>
export default {
  name: 'ProductStatus',
  props: {
    productStatus: {
      type: Object,
      required: true,
    }
  },
  computed: {
    
  }
}
</script>

<style lang="scss">
@import "../../../../styles/variables.scss";

  .product-status {
    background: blueviolet;
    flex: 1;
    margin: $spacing-md;
  }
</style>
