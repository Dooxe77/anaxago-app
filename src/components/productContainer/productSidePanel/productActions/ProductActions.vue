<template>
  <div class="product-actions">
   <Button class="action-button" @click="openProductForms">
      Investir
    </Button>
  </div>
</template>

<script>
import Button from "../../../shared/Button";

export default {
  name: 'ProductActions',
  components: {
    Button,
  }, 
  methods: {
    openProductForms() {
      this.$emit('open-product-forms');
    }
  }
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
        background-color: $teal-blue-color !important;
        padding: 20px 35px !important;
      }
    }
  }
</style>
