<template>
  <div id="app">
    <nav-section v-bind=adminInfo />
    <section>
      <div class="gauge-list-wrapper">
          <Gauge v-for="(gauge, index) in gaugeList" v-bind=gauge :key=index />
      </div>
    </section>
    <section>
      <employee-table :employeeList=employeeList />
    </section>
    <section>
      <message-board :messageList=messageList />
    </section>
  </div>
</template>

<script>
  import Gauge from './components/Gauge'
  import NavSection from './components/NavSection'
  import EmployeeTable from './components/EmployeeTable'
  import MessageBoard from './components/MessageBoard'

  export default {
    name: 'App',
    data() {
      return {
        gaugeList: [],
        employeeList: [],
        messageList: [],
        adminInfo: {},
      }
    },
    components: {
      NavSection,
      Gauge,
      EmployeeTable,
      MessageBoard,
    },
    created(){
      this.fetchGaugeList()
      this.fetchAdminInfo()
      this.fetchEmployeeList()
      this.fetchMessageList()
    },
    methods: {
      fetchGaugeList() {
        fetch('http://localhost:3000/GaugeList')
        .then(res => res.json())
        .then(data => this.gaugeList = data)
      },
      fetchAdminInfo() {
        fetch('http://localhost:3000/AdminInfo')
        .then(res => res.json())
        .then(data => this.adminInfo = data)
      },
      fetchEmployeeList() {
        fetch('http://localhost:3000/EmployeeList')
        .then(res => res.json())
        .then(data => this.employeeList = data)
      },
      fetchMessageList() {
        fetch('http://localhost:3000/MessageList')
        .then(res => res.json())
        .then(data => this.messageList = data)
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  .gauge-list-wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-top: 10px;
  }
</style>
