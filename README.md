# Vue-Slackhook

> A Vue component to implement a feedback form for users to give feedback on your application, with integration of a Slackwebhook.

## About the project

The current version of this project is 0.0.1. I intend to contribute a lot more to this package with new features and more possibilities. For now I have only tested this as a component within a Vue-loader project.

## Installation

    * Make sure to have a slack workspace available and create a new channel to recieve the feedback data
    * Login to your slack account/workspace and create a new app over [here](https://api.slack.com/apps?new_app=1)
    * Create a new incoming webhook [here](https://my.slack.com/services/new/incoming-webhook/) and retrieve the webhook URL.

After these steps run the following command

``` bash
# install dependencies
npm install vue-slackhook axios --save-dev
```

## Usage

```javascript

<script>
import { Feedback } from 'vue-slackhook'
import axios from 'axios'

export default {
    
    ...

    components: {
        Feedback
    }

    ...

};
</script>
<Template>

    <Feedback webhookUrl="WEBHOOK URL HERE" />

</Template>
```

## Options/Props

```javascript

<script>

    ...

    props: {

        //Use this prop to integrate your slack channel
        webhookUrl: {
            type: String,
            default: 'No webhook url is applied'
        },

        //Submit button text
        submitButtonText: {
            type: String,
            default: 'Send'
        },

        //Trigger button text
        buttonText: {
            type: String,
            default: '?'
        },

        //Font-awesome icon as button text (make sure to include font awesome)
        buttonFA: {
            type: Boolean,
            default: false
        },

        //Font awesome icon name (for instance user == fa fa-user)
        icon: {
            type: String,
            default: 'user'
        }

    }

    ...

</script>

<template>

    //This wil render a trigger button with the 'fa fa-question' icon and a submit button that says 'Send'
    <Feedback  submitButtonText="Send" buttonText="Feedback here" :buttonFA="true"  icon="question" />

</template>    

```

## Contribution

If you have any questions, please feel free to contact me at [twitter](https://twitter.com/glenngijsberts) or create a new issue. Feel free to use this project yourself.