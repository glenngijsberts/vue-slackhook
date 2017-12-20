<template>

  <Feedback 
  submitButtonText="Send"
  buttonText="Feedback here"
  :buttonFa="true" 
  icon="question"
  :laravel="false"
  webhookUrl="https://hooks.slack.com/services/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"
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
