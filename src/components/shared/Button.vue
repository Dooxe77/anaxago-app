<template>
  <v-btn 
    :color="color" 
    elevation="2"
    class="default-button">
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
@import "../../styles/variables.scss";

  .default-button {
    // Temp: fix important
    background-color: $teal-blue-color !important;
    padding: 20px 35px !important;
    font-size: 16px;
    text-align: center;
    line-height: 1;

    &:hover { 
      transition: all .2s ease-in-out;
    }
  }
</style>
