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
  components: {
    VTextField,
  },
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
  methods: {
    changeInputValue(value) {
      this.$emit('change', value);
    }
  }
}
</script>

<style lang="scss">

</style>
