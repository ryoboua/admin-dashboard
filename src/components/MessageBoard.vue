<template>
    <div class="col s12 l4" >
        <div class="message-container white-text hoverable z-depth-2" :style="{ backgroundColor: `${msg.color}` }" v-for="msg in messageList" :key=msg.postId>
            <div class="left-align"><i class="medium material-icons">format_quote</i></div>
            <p :style="{ marginTop: '0'}">{{ msg.body }}</p>
            <h6 class="left-align">- {{msg.author}} </h6>
        </div>
    </div>
</template>
<script>
    export default {
        name: 'MessageBoard',
        props: {
            messageList: {
                type: Array,
                default: () => [
                    {
                        postId: 1,
                        color: '#283593',
                        author: "Reggie Y",
                        body: 
                            `Lorem ipsum dolor sit amet, consectetur adipiscing elit,
                            sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                            Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
                            Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                            Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
                            `
                    }
                ]
            }
        }
    }
</script>
<style scoped>
 .message-container {
     border-radius: 5px;
     padding: 0.5em;
     margin-bottom: 0.5em;
 }
</style>
