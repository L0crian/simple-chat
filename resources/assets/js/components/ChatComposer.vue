<template>
    <div class="chat-composer">
        <input type="text" placeholder="Type something here..." v-model="messageText" @keyup.enter="sendMessage">
        <button class="btn btn-pimary" @click="sendMessage">Send</button>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                messageText:''
            }
        },
        methods: {
            sendMessage: function () {
                this.$emit('messagesent', {
                    message: this.messageText,
                    user: {
                        name: $('.navbar-right .dropdown-toggle').text()
                    }
                });
                this.messageText = '';
            }
        }
    }
</script>

<style>
    .chat-composer {
        display: flex;
    }
    .chat-composer input {
        flex: 1 auto;
        padding: .5rem 1rem;
    }
    .chat-composer button {
        border-radius: 0;
    }
</style>