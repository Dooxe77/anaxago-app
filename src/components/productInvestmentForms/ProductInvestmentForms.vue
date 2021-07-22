<template>
  <div class="product-investment-forms">
    <!-- Possibilité de mettre les différentes states dans les data et d'améliorer grandement le template  -->
    <v-stepper
      v-model="currentStep"
      vertical>
      <v-stepper-step
        :complete="currentStep > 1"
        :editable="currentStep > 1"
        step="1">
        Montant
      </v-stepper-step>
      <v-stepper-content step="1">
        <Amount-investment-step :amout="amount" @update-amount="updateAmount"/>
        <Step-form-buttons 
          :is-disabled-validate-button="isDisabledValidateButtonAmountStep"
          @validate="changeCurrentStep(2)" 
          @cancel="closeForm" />
      </v-stepper-content>
  
      <v-stepper-step 
        :complete="currentStep > 2" 
        :editable="isValidFirstStep"
        step="2">
        Compte d'investissement
      </v-stepper-step>
      <v-stepper-content step="2">
        <Investment-account-step />
        <Step-form-buttons @validate="changeCurrentStep(3)" @cancel="closeForm" />
      </v-stepper-content>
  
      <v-stepper-step 
        :complete="currentStep > 3" 
        :editable="isValidFirstStep && isValidSecondStep"
        step="3">
        Signature
      </v-stepper-step>
      <v-stepper-content step="3">
        <Signature-step />
        <Step-form-buttons @validate="changeCurrentStep(4)" @cancel="closeForm" />
      </v-stepper-content>
  
      <v-stepper-step 
        :complete="currentStep > 4"
        :editable="isValidFirstStep && isValidSecondStep && isValidThirdStep"
        step="4">
        Moyen de paiement
      </v-stepper-step>
      <v-stepper-content step="4">
        <Payment-method-step />
        <Step-form-buttons @validate="changeCurrentStep(5)" @cancel="closeForm" />
      </v-stepper-content>

      <v-stepper-step :editable="isValidFirstStep && isValidSecondStep && isValidThirdStep && isValidFourthStep" step="5">
        Résumé
      </v-stepper-step>
      <v-stepper-content step="5">
        <Summary-step :investment-data="investmentData"/>
        <Button 
          class="validate-form-button" 
          isSmall 
          @click="finishProcess">
          Valider
        </Button>
        <Button 
          isSmall 
          isText 
          elevation="0"
          @click="closeForm">
          Abandonner
        </Button>
      </v-stepper-content>
    </v-stepper>
    <v-snackbar
      absolute
      bottom
      color="primary"
      text
      :timeout="-1"
      :value="showToast">
      Investissement effectué avec succès.
    </v-snackbar>
  </div>
</template>

<script>
import { VStepperContent, VStepper, VStepperStep } from 'vuetify/lib';
import Button from '../shared/Button';
import StepFormButtons from './stepFormButtons/StepFormButtons';
import AmountInvestmentStep from './steps/AmountInvestmentStep';
import InvestmentAccountStep from './steps/InvestmentAccountStep';
import PaymentMethodStep from './steps/PaymentMethodStep';
import SignatureStep from './steps/SignatureStep';
import SummaryStep from './steps/SummaryStep';

export default {
  name: 'ProductInvestmentForms',
  data () {
    return {
      currentStep: 1,
      amount: "",
      showToast: false,
    }
  },
  components: {
    Button,
    AmountInvestmentStep,
    InvestmentAccountStep,
    PaymentMethodStep,
    SignatureStep,
    StepFormButtons,
    SummaryStep,
    VStepperContent, 
    VStepper, 
    VStepperStep,
  },
  computed: {
    isValidFirstStep() {
      return false;
    },
    isValidSecondStep() {
      return false;
    },
    isValidThirdStep() {
      return false;
    },
    isValidFourthStep() {
      return false;
    },
    isDisabledValidateButtonAmountStep() {
      const parsedAmount = parseInt(this.amount);
      return isNaN(parsedAmount) ? true : parsedAmount < 1000;
    },
    investmentData() {
      return {
        amount: this.amount,
      }
    },
  },
  methods: {
    changeCurrentStep(step) {
      this.currentStep = step;
    },
    closeForm() {
      this.$emit('close-product-forms');
    },
    finishProcess() {
      this.showToast = true;
      setTimeout(() => { 
        this.showToast = false;
      }, 8000);
    },
    updateAmount(value) {
      this.amount = value;
    },
  }
}
</script>

<style lang="scss">
@import "../../styles/variables.scss";
  .product-investment-forms {
    width: 50%;

    .validate-form-button{
      margin-right: $spacing-sm;
    }
  }
  
</style>
