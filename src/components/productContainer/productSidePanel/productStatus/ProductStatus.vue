<template>
  <div class="product-status">
    <div class="product-amount">
      <span class="product-amount-label">Montant cible</span>
      <span class="product-amount-value">{{ targetAmount }} €</span>
    </div>
    <div class="product-amount">
      <span class="product-amount-label">Montant actuel</span>
      <span class="product-amount-value">{{ currentAmount }} €</span>
    </div>
    <v-progress-circular
      :rotate="-90"
      :size="100"
      :width="15"
      :value="productStatusPercent"
      color="primary"
      class="progress-circular-amount"
      >
      <!-- // TEMP: Color primary not working -->
        {{ productStatusPercent }}%
      </v-progress-circular>
  </div>
</template>

<script>
import { VProgressCircular } from 'vuetify/lib';
export default {
  name: 'ProductStatus',
  props: {
    productStatus: {
      type: Object,
      required: true,
    }
  },
  components: {
    VProgressCircular,
  },
  computed: {
    targetAmount() {
      return this.productStatus.targetAmount;
    },
    currentAmount() {
      return this.productStatus.currentAmount;
    },
    parsedTargetAmount() {
      return this.parsedAmount(this.targetAmount);
    },
    parsedCurrentAmount() {
      return this.parsedAmount(this.currentAmount);
    },
    productStatusPercent() {
      return ((this.parsedCurrentAmount * 100) / this.parsedTargetAmount).toFixed(2);
    },
  },
  methods: {
    parsedAmount(amount) {
      if(!amount) return 0;
      const parsedAmount = parseInt(amount.replace(/ /g,''));
      return isNaN(parsedAmount) ? 0 : parsedAmount;
    }
  }
}
</script>

<style lang="scss">
@import "../../../../styles/variables.scss";
@import "~vuetify/src/styles/settings/variables";

  .product-status {
    margin: $spacing-md;
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;

    .product-amount {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      line-height: 1.7;

      .product-amount-label {
        font-size: 15px;
        font-weight: 600;
        color: $cutty-sark-color;
      }

      .product-amount-value {
        color: $oxford-blue-color;
        font-size: 18px;
        font-weight: 600;
      }
    }

    .progress-circular-amount{
      margin-top: 20px;
    }
  }
</style>
