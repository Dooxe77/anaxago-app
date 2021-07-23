<template>
  <div class="payment-method-step">
    <Select 
      label="Moyen de paiement" 
      :items="paymentMethods" 
      @select="updateSelectedPaymentMethod" />
  </div>
</template>

<script>
import Select  from "../../shared/Select";

export default {
  name: 'PaymentMethodStep',
  components: {
    Select,
  },
  data () {
    return {
      paymentMethods: [
        "Paypal",
        "Carte de crédit",
        "Virement"
      ],
    }
  },
  methods: {
    updateSelectedPaymentMethod(value) {
      this.$emit('update-selected-payment-method', value);
    }
  },
}
</script>

<style lang="scss">

</style>
