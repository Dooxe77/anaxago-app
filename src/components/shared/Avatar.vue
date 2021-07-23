<template>
  <v-avatar :color="color" :size="size">
    <slot></slot>
  </v-avatar>
</template>

<script>
import { VAvatar } from 'vuetify/lib';

export default {
  name: 'Avatar',
  components: {
    VAvatar,
  },
  props: {
    color: {
      type: String,
      default: "primary",
    },
    size: {
      type: Number, 
      default: 50,
    }
  },
}
</script>

<style lang="scss">

</style>
