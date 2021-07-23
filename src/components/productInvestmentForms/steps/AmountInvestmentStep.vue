<template>
  <div>
    <Text-input 
      label="Montant que vous souhaitez investir"
      prefix="€"
      :value="amount"
      :rules="[rules.required, rules.minimum]"
      @change="updateAmount"
    />
  </div>
</template>

<script>
import TextInput from '../../shared/TextInput';

export default {
  name: 'AmountInvestmentStep',
  components: {
    TextInput,
  },
  props: {
    amount: {
      type: String,
    },
  },
  data () {
    return {
      rules: {
        required: value => !!value || 'Requis.',
        minimum: value => value >= 1000 || 'Minimum 1000€',
      }
    }
  },
  methods: {
    updateAmount(value) {
      this.$emit('update-amount', value);
    }
  },
}
</script>

<style lang="scss">
@import "../../../styles/variables.scss";

</style>
