<template>
  <div class="physical-person-form">
    <Text-input 
      label="Siret"
      :value="siret"
      :rules="[rules.required]"
      @change="updateData('siret', $event)"
    />
    <Text-input 
      label="Raison sociale"
      :value="socialReason"
      :rules="[rules.required]"
      @change="updateData('social-reason', $event)"
    />
  </div>
</template>

<script>
import TextInput from "../../../shared/TextInput";

export default {
  name: 'MoralPersonForm',
  components: {
    TextInput,
  },
  props: {
    moralPersonInfos: Object,
  },
  data() {
    return {
      rules: {
        required: value => !!value || 'Requis.',
      }
    }
  },
  computed: {
    siret() {
      return this.moralPersonInfos.siret;
    },
    socialReason() {
      return this.moralPersonInfos.socialReason;
    },
  },
  methods: {
    updateData(eventName, value) {
      this.$emit(`update-${eventName}`, value);
    }
  }
}
</script>

<style lang="scss">

</style>
