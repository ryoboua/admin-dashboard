<template>
    <div>
        <div v-for="msg in messageList" :key=msg.postId>
            <p>{{ msg.body }}</p>
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

</style>
