<template>
  <v-progress-circular
    :rotate="-90"
    :size="100"
    :width="15"
    :value="value"
    class="progress-circular">
    {{ displayedValue }}
  </v-progress-circular>
</template>

<script>
import { VProgressCircular } from 'vuetify/lib';
export default {
  name: 'ProgressCircular',
  components: {
    VProgressCircular,
  },
  props: {
    value: {
      type: String,
      required: true,
    }
  },
  computed: {
    displayedValue() {
      return `${this.value} %`;
    }
  },
}
</script>

<style lang="scss">
@import "../../styles/variables.scss";

.progress-circular {
  color: $genoa-color;
}
</style>
