<template>
  <V-text-field
    :label="label"
    :value="value"
    :prefix="prefix"
    :rules="rules"
    @input="changeInputValue"/>
</template>

<script>
import { VTextField } from 'vuetify/lib';

export default {
  name: 'TextInput',
  props: {
    label: {
      type: String,
      required: true,
    },
    value: {
      type: String,
    },
    prefix: {
      type: String,
    },
    rules: {
      type: Array,
    }
  },
  components: {
    VTextField,
  },
  methods: {
    changeInputValue(value) {
      this.$emit('change', value);
    }
  }
}
</script>

<style lang="scss">

</style>
