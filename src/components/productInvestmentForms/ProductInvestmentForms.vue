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
        Moyen de paiement
      </v-stepper-step>
      <v-stepper-content step="3">
        <Payment-method-step @update-selected-payment-method="updateSelectedPaymentMethod"/>
        <Step-form-buttons 
          :is-disabled-validate-button="isDisabledValidateButtonPaymentMethodStep"
          @validate="changeCurrentStep(4)" 
          @cancel="closeForm" />
      </v-stepper-content>

      <v-stepper-step :editable="isValidFirstStep && isValidSecondStep" step="4">
        Validation finale
      </v-stepper-step>
      <v-stepper-content step="4">
        <Summary-step :investment-data="investmentData"/>
        <Text-input 
          v-if="showValidationInput"
          label="Code reçu par sms"
          v-model="phoneMessageCode"
        />
        <Button 
          v-if="showValidationInput"
          class="confirm-form-button" 
          isSmall 
          @click="validateInvestment">
          Valider l'investissement
        </Button>
        <Button 
          v-else-if="!showValidationInput"
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
      :value="showToast">
      Envoi du code de validation effectué avec succès.
    </v-snackbar>
    <v-snackbar
      absolute
      bottom
      color="green"
      text
      :value="showProcessToast">
      Processus terminé
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
import SummaryStep from './steps/SummaryStep';
import TextInput from '../shared/TextInput';

export default {
  name: 'ProductInvestmentForms',
  data () {
    return {
      currentStep: 1,
      amount: "",
      paymentMethod: "",
      showToast: false,
      showProcessToast: false,
      showValidationInput: false,
      phoneMessageCode: "543-380",
    }
  },
  components: {
    Button,
    AmountInvestmentStep,
    InvestmentAccountStep,
    PaymentMethodStep,
    StepFormButtons,
    SummaryStep,
    TextInput,
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
    isDisabledValidateButtonAmountStep() {
      const parsedAmount = parseInt(this.amount);
      return isNaN(parsedAmount) ? true : parsedAmount < 1000;
    },
    isDisabledValidateButtonPaymentMethodStep() {
      return !this.paymentMethod;
    },
    investmentData() {
      return {
        amount: this.amount,
        paymentMethod: this.paymentMethod,
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
      setTimeout(() => { 
        this.showToast = true;
        this.showValidationInput = true;
      }, 1000);

      setTimeout(() => { 
        this.showToast = false;
      }, 10000);
    },
    updateAmount(value) {
      this.amount = value;
    },
    updateSelectedPaymentMethod(value) {
      this.paymentMethod = value;
    },
    validateInvestment() {
      setTimeout(() => { 
        this.showProcessToast = true;
      }, 1000);

      setTimeout(() => { 
        this.showProcessToast = false;
      }, 10000);
    },
  }
}
</script>

<style lang="scss">
@import "../../styles/variables.scss";
  .product-investment-forms {
    width: 50%;

    .validate-form-button, .confirm-form-button{
      margin-right: $spacing-sm;
    }
  }
  
</style>
