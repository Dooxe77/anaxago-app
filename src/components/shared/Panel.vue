<template>
  <div class="panel">
    <slot></slot>
  </div>
</template>

<script>

export default {
  name: 'Panel',
}
</script>

<style lang="scss">
  @import "../../styles/variables.scss";

  .panel {
    border-radius: $radius-sm;
    border: 1px solid #e8ebef;
  }
</style>
