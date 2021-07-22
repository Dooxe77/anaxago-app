<template>
  <div class="payment-method-step">
    <v-select 
      label="Moyen de paiement" 
      :items="paymentMethods" 
      @input="updateSelectedPaymentMethod" />
  </div>
</template>

<script>
import { VSelect } from "vuetify/lib";

export default {
  name: 'PaymentMethodStep',
  data () {
    return {
      paymentMethods: [
        "Paypal",
        "Carte de crédit",
        "Virement"
      ],
    }
  },
  components: {
    VSelect,
  },
  methods: {
    updateSelectedPaymentMethod(value) {
      this.$emit('update-selected-payment-method', value);
    }
  },
}
</script>

<style lang="scss">
@import "../../../styles/variables.scss";

</style>
