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
  components: {
  },
  computed: {
    
  },
  methods: {

}
}
</script>

<style lang="scss">
@import "../../../styles/variables.scss";

</style>
