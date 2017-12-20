# Vue-Slackhook

> A Vue component to implement a feedback form for users to give feedback on your application, with integration of a Slackwebhook.

## About the project

The current version of this project is 0.0.1. I intend to contribute a lot more to this package with new features and more possibilities. For now I have only tested this as a component within a Vue-loader project.

## Installation

- Make sure to have a slack workspace available and create a new channel to recieve the feedback data

- Login to your slack account/workspace and create a new app over [here](https://api.slack.com/apps?new_app=1)

- Create a new incoming webhook [here](https://my.slack.com/services/new/incoming-webhook/) and retrieve the webhook URL.

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
        buttonFa: {
            type: Boolean,
            default: false
        },

        //Font awesome icon name (for instance user == fa fa-user)
        icon: {
            type: String,
            default: 'user'
        },
        
        //Set this prop to true to activate a pre-defined theme
        theme: {
            type: Boolean,
            default: false
        }

    }

    ...

</script>

<template>

    //This wil render a trigger button with the 'fa fa-question' icon and a submit button that says 'Send'
    <Feedback  submitButtonText="Send" buttonText="Feedback here" :buttonFA="true"  icon="question" />

</template>    

```

## Using Laravel

In your `app.js`

```javascript

Vue.component('feedback', require('vue-slackhook'));

```

#### camelCase vs kebab-case

It is possible that your props are not working. Instead of writing your props camelCase you must write them kebab-case. You can read more [here](https://vuejs.org/v2/guide/components.html#camelCase-vs-kebab-case). 

Example: `<Feedback button-text="Feedback here" :button-fa=true icon="question" submit-button-text="Post!" />`

#### Props for Laravel

There are `props` available specific for the Laravel framework.

```javascript
        //If true props page and user will be included for sending to slack
        laravel: {
            type: Boolean,
            default: false
        },
        
        //Use this prop with the currentRouteName() function to send the current route
        page: {
            type: String,
            default: 'No page found'
        },
        
        //Use this prop with the Auth::user()->username function to send the logged in user
        user: {
            type: String,
            default: 'No user found'
        }

```

## Styling

Besides the pre-defined theme this component has CSS classes on different elements to style the component. All CSS classes will be available soon.

## Contribution

If you have any questions, please feel free to contact me at [twitter](https://twitter.com/glenngijsberts) or create a new issue. Feel free to use this project yourself.