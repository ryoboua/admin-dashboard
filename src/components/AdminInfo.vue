<template>
    <div class="col s12 l4 mt-20">
        <Bars
            :data=tableData
            :gradient="['#6fa8dc', '#42b983']"
            :style="{ maxWidth: '450px'}"
            >
        </Bars>
        <p class="mr"> <span class="green-text">${{ totalIncome }}</span> Total Income</p>
        <p class="mr"> <span class="blue-text">{{ activeUsers }}</span> Active Users</p>
    </div>
</template>
<script>
    import Bars from 'vuebars'

    export default {
        name: 'AdminInfo',
        props: {
            name: {
                type: String,
                default: 'Default Name'
            },
            imgURL: {
                type: String,
                default: 'Default Name'
            },
            totalIncome: {
                    type: Number,
                    default: 34,
            },
            activeUsers: {
                type: Number,
                default: 20
            },
            notification: {
                type: Number,
                default: 0
            },
            messages: {
                type: Number,
                default: 4
            },
            tableData: {
                type: Array,
                default: () => [1, 2, 5, 9, 5, 10, 3, 5, 2, 5, 1, 8, 2, 9, 0]
            }
        },
        components: {
            Bars,
        }
    }
</script>
<style scoped>
 .mt-20 {
     margin-top: 20px;
 }
</style>

