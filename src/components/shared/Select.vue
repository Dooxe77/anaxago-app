<template>
  <v-select 
    :label="label" 
    :items="items" 
    @input="selectValue" />
</template>

<script>
import { VSelect } from 'vuetify/lib';

export default {
  name: 'SelectInput',
  components: {
    VSelect,
  },
  props: {
    label: {
      type: String,
      required: true,
    },
    items: {
      type: Array,
      required: true,
    },
  },
  methods: {
    selectValue(value) {
      this.$emit('select', value);
    }
  }
}
</script>

<style lang="scss">

</style>
