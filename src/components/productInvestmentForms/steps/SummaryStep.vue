<template>
  <Panel class="summary-step">
    <div 
      v-for="item in summaryInfos" 
      class="summary-info"
      :key="item.id">
      <span class="key">
        {{item.label}}
      </span>
      <span class="value">
        {{item.value}}
      </span>
    </div>
  </Panel>
</template>

<script>
import Panel from '../../shared/Panel';

export default {
  name: 'SummaryStep',
  components: {
    Panel,
  },
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
    amount() {
      return `${this.investmentData.amount} €`;
    },
    paymentMethod() {
      return this.investmentData.paymentMethod;
    },
    investmentType() {
      return this.investmentData.investmentType.type;
    },
    personName() {
      return `${this.investmentData.investmentType.infos.firstName} ${this.investmentData.investmentType.infos.lastName}`;
    },
    siret() {
      return this.investmentData.investmentType.infos.siret;
    },
    socialReason() {
      return this.investmentData.investmentType.infos.socialReason;
    },
    summaryInfos() {
      const infos = [
        {
          label: 'Montant: ',
          value: this.amount,
          id: 'AMOUNT',
        },
        {
          label: 'Méthode de paiement: ',
          value: this.paymentMethod,
          id: 'PAYMENT_METHOD',
        },
        {
          label: 'Porteur de l\'investissement:',
          value: this.investmentType,
          id: 'INVESTMENT_TYPE',
        },
      ];

      if (this.investmentType === 'Personne physique') {
        infos.push({
          label: 'Identité: ',
          value: this.personName,
          id: 'IDENTITY',
        });
      } else if(this.investmentType === 'Personne morale') {
        infos.push({
          label: 'Siret: ',
          value: this.siret,
          id: 'SIRET',
        });
        infos.push({
          label: 'Raison sociale: ',
          value: this.socialReason,
          id: 'SOCIAL_REASON',
        });
      }
      return infos;
    }
  },
  methods: {

  }
}
</script>

<style lang="scss">
@import "../../../styles/variables.scss";

  .summary-step {
    margin-bottom: $spacing-lg;

    .summary-info {
      margin: $spacing-md;

      .key {
        line-height: 1.9;
        color: $cutty-sark-color;
      }

      .value {
        display: flex;
        line-height: 1.5;
        color: $nile-blue-color;
      }
    }
  }
</style>
