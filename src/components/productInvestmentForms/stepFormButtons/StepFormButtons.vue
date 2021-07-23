<template>
  <div>
    <Button 
      class="validate-button" 
      isSmall 
      :is-disabled="isDisabledValidateButton"
      @click="onClickValidateButton">
      Continuer
    </Button>
    <Button 
      isSmall 
      isText 
      elevation="0"
      @click="onClickCancelButton">
      Annuler
    </Button>
  </div>
</template>

<script>
import Button from '../../shared/Button';

export default {
  name: 'StepFormButtons',
  components: {
    Button,
  },
  props: {
    isDisabledValidateButton: { 
      type: Boolean, 
    }
  },
  data () {
    return {
      currentStep: 1,
    }
  },
  methods: {
    onClickValidateButton() {
      this.$emit('validate');
    },
    onClickCancelButton() {
      this.$emit('cancel');
    },
  }
}
</script>

<style lang="scss">
@import "../../../styles/variables.scss";

.validate-button {
  margin-right: $spacing-sm;
}
  
</style>
