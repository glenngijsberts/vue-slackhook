<template>
    
    <div class="feedback-container">

        <form class="feedback-form" @submit.prevent="checkForm()" v-show="formShow">

            <span class="close-form" @click="toggleForm()">&#10006;</span>

            <div class="group">
                <label for="name">Name</label>
                <input type="text" id="name" class="input" v-model="name">
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

        <button @click="toggleForm()"><span class="button-text" v-if="!this.buttonFA">{{ this.buttonText }}</span><span class="button-icon" v-else><i :class="fontAwesome"></i></span></button>

    
    </div>

</template>

<script>

import axios from 'axios'

export default {

    name: 'feedback',

    props: {

        webhookUrl: {
            type: String,
            default: 'No webhook applied'
        },

        submitButtonText: {
            type: String,
            default: 'Send'
        },

        buttonText: {
            type: String,
            default: '?'
        },

        buttonFA: {
            type: Boolean,
            default: false
        },

        icon: {
            type: String,
            default: 'user'
        }

    },

    data() {
        return {
            name: '',
            subject: '',
            description: '',

            formShow: false
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
            
            let url = this.webhookUrl;
            let text = 'test again'

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
            
        },

        checkForm() {
            
            this.name  == '' || this.subject == '' || this.description == '' ? alert('All fields are required') : this.storeData();
            
        }

    },

    created() {



    },

    computed: {

        fontAwesome(){

            let icon = this.icon;

            return `fa fa-${icon}`
        }

    }
  
}
</script>

<style lang="scss" scoped>

    .feedback-container {

        position: fixed;
        right: 20px;
        bottom: 20px;

        .feedback-form {

            position: absolute;
            bottom: 20px;
            right: 0px;

            background-color: lightgrey;
            padding: 40px;
            border: 1px solid grey;
            border-radius: 4px;

            .close-form {
                position: absolute;
                right: 10px;
                top: 10px;
                cursor: pointer;
            }

        }

    }

</style>
