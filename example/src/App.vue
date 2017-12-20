<template>

  <Feedback 
  submitButtonText="Send"
  buttonText="Feedback here"
  :buttonFa="true" 
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
