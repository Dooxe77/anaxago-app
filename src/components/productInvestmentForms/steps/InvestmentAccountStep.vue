<template>
  <div class="investment-account-step">
    <Select 
      label="Choix du type d'investissement"
      :items="investmentTypeList" 
      @select="selectInvestment"
    />
    <Physical-person-form 
      v-if="isPhysicalPerson"
      :physical-person-infos="physicalPersonInfos"
      @update-first-name="updateFirstName"
      @update-last-name="updateLastName"/>
    <Moral-person-form 
      v-else-if="isMoralPerson"
      :moral-person-infos="moralPersonInfos"
      @update-siret="updateSiret"
      @update-social-reason="updateSocialReason"/>
    <Pea-form v-else-if="isPEA"/>
  </div>
</template>

<script>
import Select from '../../shared/Select'
import PhysicalPersonForm from './investmentAccountForms/PhysicalPersonForm';
import MoralPersonForm from './investmentAccountForms/MoralPersonForm';
import PeaForm from './investmentAccountForms/PeaForm';

export default {
  name: 'InvestmentAccountStep',
  components: {
    MoralPersonForm,
    PeaForm,
    PhysicalPersonForm,
    Select,
  },
  props: {
    investmentType: String,
    physicalPersonInfos: Object,
    moralPersonInfos: Object,
  },
  data () {
    return {
      investmentTypeList: [
        "Personne physique",
        "Personne morale",
        "PEA"
      ],
    }
  },
  computed: {
    isPhysicalPerson() {
      return this.investmentType === 'Personne physique';
    },
    isMoralPerson() {
      return this.investmentType === 'Personne morale';
    },
    isPEA() {
      return this.investmentType === 'PEA';
    },
  },
  methods: {
    selectInvestment(value) {
      this.$emit('select-investment', value);
    },
    // Possibilité de fire une méthode générique ici pour tous les emits.
    // Personne physique ( avec un state management ça aurait été beaucoup mieux )
    updateFirstName(value) {
      this.$emit('update-first-name', value);
    },
    updateLastName(value) {
      this.$emit('update-last-name', value);
    },
    // Personne moral
    updateSiret(value) {
      this.$emit('update-siret', value);
    },
    updateSocialReason(value) {
      this.$emit('update-social-reason', value);
    },
  }
}
</script>

<style lang="scss">
@import "../../../styles/variables.scss";

</style>
