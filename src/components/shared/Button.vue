<template>
  <v-btn 
    :color="color"
    :elevation="elevation"
    :text="isText"
    :small="isSmall"
    :disabled="isDisabled"
    @click="onClickButton"> 
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
    elevation: {
      type: String,
      default: "2",
    },
    isText: {
      type: Boolean,
    },
    isSmall: {
      type: Boolean,
    },
    isDisabled: {
      type: Boolean,
    }
  },
  components: {
    VBtn,
  },
  computed: {
  },
  methods: {
    onClickButton() {
      this.$emit('click');
    }
  }
}
</script>

<style lang="scss">
@import "../../styles/variables.scss";
  
  .default-button {
    font-size: 16px;
    text-align: center;
    line-height: 1;

    &:hover { 
      transition: all .2s ease-in-out;
    }
  }
</style>
