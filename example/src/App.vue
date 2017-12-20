<template>

  <Feedback 
  submitButtonText="Send"
  buttonText="?"
  :buttonFa="false" 
  icon="question"
  webhookUrl="https://hooks.slack.com/services/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"
  :theme="true"
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
