<template>
  <div>
    {{ JSON.stringify(investmentData) }}
  </div>
</template>

<script>
export default {
  name: 'SummaryStep',
  props: {
    investmentData: {
      type: Object,
      required: true,
    },
  },
  data () {
    return {

    }
  },
  computed: {
    
  },
  methods: {

  }
}
</script>

<style lang="scss">

</style>
