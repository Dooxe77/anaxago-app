<template>
  <div class="contact-infos">
    <div class="contact-avatar">
      <Avatar>
        <img src="https://i.pravatar.cc/50" alt="avatar" />
      </Avatar>
    </div>
    <div class="contact-details">
      <div class="help-message">
        Besoin d'aide ?
      </div>
      <div class="info-message">
        <span class="underline italic">Contact:</span> 
        {{productContact.name}}
      </div>
      <div class="info-message">
        <span class="underline italic">Tél:</span> 
        {{productContact.phoneNumber}}
      </div>
      <div class="info-message">
        <span class="underline italic">Mail:</span> 
        {{productContact.mail}}
      </div>
    </div>
  </div>
</template>

<script>
import Avatar from "../../../shared/Avatar";

export default {
  name: 'ContactInfos',
  props: {
     productContact: {
      type: Object,
      required: true,
    }
  },
  components: {
    Avatar,
  },
}
</script>

<style lang="scss">
@import "../../../../styles/variables.scss";

  .contact-infos {
    display: flex;

    .contact-avatar {
      display: flex;
      align-items: center;
      margin: 0 $spacing-sm;
    }

    .contact-details {
      margin: 0 $spacing-sm;

      .help-message {
        color: $firefly-color;
        font-size: $font-size-text;
        line-height: 1.7;
      }

      .info-message {
        font-size: $font-size-text-md;
        line-height: 1.7;
        color: $cutty-sark-color;
      }
    }
  }
</style>
