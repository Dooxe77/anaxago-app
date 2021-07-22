<template>
  <div class="product-actions">
   <Button class="action-button">Investir</Button>
  </div>
</template>

<script>
import Button from "../../../shared/Button";

export default {
  name: 'ProductActions',
  components: {
    Button,
  }, 
}
</script>

<style lang="scss">
@import "../../../../styles/variables.scss";

  .product-actions {
    padding: $spacing-lg;
    display: flex;
    justify-content: center;

    .action-button {
      &.v-btn {
        height: 50px;
      }
    }
  }
</style>
