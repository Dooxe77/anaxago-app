<template>
  <v-btn 
    :color="color" 
    elevation="2">
    <slot></slot>
  </v-btn>
</template>

<script>
import { VBtn } from 'vuetify/lib';

export default {
  name: 'Button',
  props: {
    color: {
      type: String,
      default: "primary",
    },
  },
  components: {
    VBtn,
  },
  
}
</script>

<style lang="scss">

</style>
