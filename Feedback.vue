<template>
    
    <div class="feedback-container" :class="{ themeApplied : this.theme }">

        <form class="feedback-form" @submit.prevent="checkForm()" v-show="formShow">

            <span class="close-form" @click="toggleForm()">&#10006;</span>

            <div v-if="!this.laravel">

                <div class="group">
                    <label for="name">Name</label>
                    <input type="text" id="name" class="input" v-model="name">
                </div>

            </div>

            <div class="group">
                <label for="name">Subject</label>
                <input type="text" id="subject" class="input" v-model="subject">
            </div>

            <div class="group">
                <label for="description">Feedback</label>
                <textarea id="description" class="input" v-model="description"></textarea>
            </div>

            <button type="submit" class="submit-button">{{ this.submitButtonText }}</button>
 
        </form>    

        <button @click="toggleForm()"><span class="button-text" v-if="!this.buttonFa">{{ this.buttonText }}</span><span class="button-icon" v-else><i :class="fontAwesome"></i></span></button>

    
    </div>

</template>

<script>

import axios from 'axios'

export default {

    name: 'feedback',

    props: {

        webhookUrl: {
            type: String,
            default: 'No webhook url is applied'
        },

        submitButtonText: {
            type: String,
            default: 'Send'
        },

        buttonText: {
            type: String,
            default: '?'
        },

        buttonFa: {
            type: Boolean,
            default: false
        },

        icon: {
            type: String,
            default: 'user'
        },

        theme: {
            type: Boolean,
            default: false
        },

        laravel: {
            type: Boolean,
            default: false
        },

        page: {
            type: String,
            default: 'No page found'
        },

        user: {
            type: String,
            default: 'No user found'
        }

    },

    data() {
        return {
            name: '',
            subject: '',
            description: '',

            formShow: false,

        }
    },

    methods: {

        toggleForm() {

            this.formShow = ! this.formShow;

        },

        clearData() {

            this.name = ''; this.subject = ''; this.description = '';
            this.formShow = false;

            alert('Feedback is submitted');

        },

        storeData() {

            if (this.webhookUrl == 'No webhook url is applied') {

                alert('Error! The form has not been submitted.');
                console.log('Developer: There is no webhook applied to the form')

            } else {
            
            let url = this.webhookUrl;
            let name = this.name;
            let subject = this.subject;
            let description = this.description;
            let user = this.user;
            let page = this.page;

            if (!this.laravel) {
                var text = `Feedback from ${name} with the subject ${subject} with the description ${description}`
            } else {
                var text = `Feedback from ${user} with the subject ${subject} with the description ${description} on page ${page}`
            }

            axios({
                data: 'payload=' + JSON.stringify({
                    "text": text
                }),
                dataType: 'json',
                processData: false,
                method: 'POST',
                url: url
            });

            this.clearData();

            }
            
        },

        checkForm() {

            if (!this.laravel) {
            
            this.name  == '' || this.subject == '' || this.description == '' ? alert('All fields are required') : this.storeData();

            } else {

                this.subject == '' || this.description == '' ? alert('All fields are required') : this.storeData();

            }
            
        }

    },

    created() {



    },

    computed: {

        fontAwesome(){

            let icon = this.icon;

            return `fa fa-${icon}`
        },


    }
  
}
</script>

<style scoped>

    .feedback-container {

        position: fixed;
        right: 20px;
        bottom: 20px;
    }

    .feedback-container .feedback-form {

        position: absolute;
        bottom: 20px;
        right: 0px;

        background-color: lightgrey;
        padding: 40px;
        border: 1px solid grey;
        border-radius: 4px;

        }

    .feedback-container .feedback-form .close-form {
        position: absolute;
        right: 10px;
        top: 10px;
        cursor: pointer;
    }

    .themeApplied button {
        background-color: #002b38;
        position: fixed;
        color: white;
        text-align: center;
        right: 20px;
        bottom: 20px;
        padding: 5px 15px 5px 15px;
        border: 1px solid #02b6df;
        border-radius: 4px;
        font-size: 22px;
        cursor: pointer;
    }

    .themeApplied.feedback-container .feedback-form {
        position: absolute;
        bottom: -10px;
        right: -10px;
        background-color: #f7f7f7;
        padding: 60px;
        border: 2px solid #d4d4d4;
        border-radius: 4px;
        width: 800px;
    }

    .themeApplied.feedback-container .feedback-form .group {
        margin-bottom: 20px;
    }

    .themeApplied.feedback-container .feedback-form .group input, .themeApplied.feedback-container .feedback-form .group textarea {
        width: 100%;
        padding: 5px 10px 5px 10px;
        border: 2px solid #d4d4d4;
        font-size: 16px;
        border-radius: 4px;
        height: 28px;
    }

    .themeApplied.feedback-container .feedback-form .group textarea {
        height: auto;
        padding: 10px;
    }



    .themeApplied.feedback-container .feedback-form .group label {
        display: block;
        margin-bottom: 10px;
        font-size: 16px;
        font-weight: bold;
        font-family: sans-serif;
    }

    .themeApplied.feedback-container .feedback-form .submit-button {
        background-color: #002b38;
        position: relative;
        color: white;
        text-align: center;
        right: 0px;
        bottom: 0px;
        padding: 10px 15px 10px 15px;
        border: 1px solid #02b6df;
        border-radius: 4px;
        font-size: 16px;
        cursor: pointer;
    }



</style>
