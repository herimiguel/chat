<template>
    <div class="chat-app">
        <Conversation :contact="selectedContact" :messages="messages"/>
        <ContactsList :contacts ="contacts" @selected="startConversationWith" /> 

    </div>
</template>

<script>
    import Conversation from './Conversation';
    import ContactsList from './ContactsList';

    export default {
        props:{
            user: {
                type: Object,
                require: true,
            }
        },
        data(){
            return {
                selectedContact: null,
                messages: [],
                contacts: [],
            };
        },
        mounted() {
            console.log(this.user);
          axios.get('/contacts').then((response) =>{
              this.contacts = response.data;
          });
        },
        methods: {
            startConversationWith(contact) {
                axios.get(`/conversation/${contact.id}`).then((response) => {
                    this.messages = response.data;
                    this.selectedContact = contact;

                });
            }
        },
         
        components: {Conversation, ContactsList }
    }
</script>
