<template>

  <Feedback 
  webhookUrl="https://hooks.slack.com/services/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"
  submitButtonText="Send"
  buttonText="Feedback here"
  :buttonFA="true" 
  icon="question"
   />

</template>

<script>

import Feedback from './components/Feedback.vue'

export default {
  name: 'app',

  components: {
    Feedback
  },

  data () {
    return {

    }
  }
}
</script>

<style lang="scss">

</style>
