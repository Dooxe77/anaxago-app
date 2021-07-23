<template>
  <div class="physical-person-form">
    <Text-input 
      label="Prénom"
      :value="firstName"
      :rules="[rules.required]"
      @change="updateData('first-name', $event)"
    />
    <Text-input 
      label="Nom"
      :value="lastName"
      :rules="[rules.required]"
      @change="updateData('last-name', $event)"
    />
  </div>
</template>

<script>
import TextInput from "../../../shared/TextInput";

export default {
  name: 'PhysicalPersonForm',
  components: {
    TextInput,
  },
  props: {
    physicalPersonInfos: Object,
  },
  data() {
    return {
      rules: {
        required: value => !!value || 'Requis.',
      }
    }
  },
  computed: {
    firstName() {
      return this.physicalPersonInfos.firstName;
    },
    lastName() {
      return this.physicalPersonInfos.lastName;
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
