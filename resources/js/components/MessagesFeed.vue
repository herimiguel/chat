<template>
    <div class="feed">
        <ul v-if="contact" >
            <li v-for="message in messages" :class="`messageA${message.to == contact.id ? 'sent' : 'recieved'}`" :key="message.id">
                <div class="text">
                    {{message.text}}
                </div>
            </li>
        </ul>
    </div>
</template>
<script>
export default {
    props: {
        contact: {
            type: Object,
            // require: true,
        },
        messages: {
            type: Array,
            require: true,
        }
    },
    
}
</script>

