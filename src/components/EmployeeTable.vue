<template>
      <table class="striped highlight responsive-table">
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
            <td>{{ e.name }}</td>
            <td>{{ e.name }}</td>
            <td>{{ e.designation }}</td>
            <td>{{ e.status }}</td>
            <td>{{ e.performance }}</td>
          </tr>
        </tbody>
      </table>
</template>
<script>
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
        
    }
</script>
<style scoped>

</style>

