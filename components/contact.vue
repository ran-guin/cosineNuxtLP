<template lang='pug'>
  v-container
    h1.primary-colour Contact Information
    hr
    p &nbsp;
    div
      v-card.darkShadow
        v-container
          v-card-text
            h2 Email: rguin@cosinesystems.org
            h2 Phone: 604-731-1124
            div.input-lg
              p &nbsp;
              p If you are interested in finding out more about how we may be able to help your organization, feel free to contact us to discuss options.
              p If you are interested in getting involved, feel free to drop us a line and let us know what it is that you are most passionate about and how you would like to contribute.
</template>

<script>
export default {
  name: 'Contact',
  components: {},
  data () {
    return {}
  }
}
</script>
