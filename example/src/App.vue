<template>

  <Feedback 
  submitButtonText="Send"
  buttonText="?"
  :buttonFa="false" 
  icon="question"
  :theme="true"
  labelName="Naam"
  labelSubject="Onderwerp"
  labelDescription="Bericht"
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
