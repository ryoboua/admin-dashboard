<template>
    <div class="col s12 l8 white table-container z-depth-2">
        <h5 class="left-align pl-1"><strong>Employee</strong> List</h5>
        <div class="divider"></div>
        <collapse :selected="true">
            <div slot="collapse-body">
            <table class="highlight responsive-table centered">
                <thead>
                <tr>
                    <th>User</th>
                    <th>Name</th>
                    <th>Designation</th>
                    <th>Status</th>
                    <th>Performance</th>
                </tr>
                </thead>
                <tbody>
                <tr v-for="e in employeeList" :key=e.id>
                    <td><img class="circle" :src="e.img" :alt="e.name"></td>
                    <td>{{ e.name }}</td>
                    <td>{{ e.designation }}</td>
                    <td :style="{ color: `${getStatusColor(e.status)}` }" >{{ e.status }}</td>
                    <td>{{ e.performance }}</td>
                </tr>
                </tbody>
            </table>
            <div slot="collapse-header">
            </div>
            </div>
        </collapse>
     </div>
</template>
<script>

    import Collapse from './Collapse'

    export default {
        name: 'EmployeeTable',
        props: {
            employeeList: {
                type: Array,
                default: () => [
                    {
                        id: 0,
                        name: 'Reggie',
                        designation: 'Developer',
                        status: 'available',
                        performance: 100
                    },
                ]
            },
        },
        components: {
            Collapse
        },
        methods: {
            getStatusColor(status){
                switch(status) {
                    case 'Available':
                    return 'green'
                    break
                    case 'Break':
                    return 'purple'
                    break
                    case 'Leave':
                    return 'Orange'
                    break
                    case 'Resigned':
                    return 'red'
                    break
                    default:
                    return 'black'
                }
            }
        }
        
    }
</script>
<style scoped>
 .table-container {
    border-radius: 5px;
    padding: 1em 0;
    margin-bottom: 1rem;
}
.pl-1 {
    padding-left: 1.6%;
}
</style>

