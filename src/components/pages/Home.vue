<template>
  <div class="message">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      msg: 'Welcome to my new app',
    };
  },
}
</script>

<style scoped>
  .message {
    font-weight: bold;
  }
</style>
