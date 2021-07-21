<template>
  <header class="header">
    <img 
      :src="logoUrl" 
      class="logo"
      alt="logo Anaxago" 
      width="130" 
      height="18">
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      logoUrl: 'https://www.anaxago.com/assets/images/logo_anaxago_blue.ceff523e.svg',
    };
  },
}
</script>

<style lang="scss">
@import "../../styles/variables.scss";

  .header {
    display: flex;
    align-items: center;
    height: 80px;
    color: $blue-dark-color;
    border-bottom: 1px solid $grey-light-color;
    margin: 0 $spacing-lg;
  }
</style>
