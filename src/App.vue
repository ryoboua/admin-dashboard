<template>
  <div id="app">
    <nav-section v-bind=adminInfo />
    <section>
      <div class="row">
        <GaugeCarousel :gaugeList=gaugeList />
        <AdminInfo v-bind=adminInfo />
      </div>
    </section>
    <section class="section-container" >
      <div class="row">
        <employee-table :employeeList=employeeList />
        <message-board :messageList=messageList />
      </div>
    </section>
    <footer class="pb-1">
        <img src='./assets/programming.svg' height="137.5" width="137.5" />
        <h6>Coded by Reggie in 2018</h6>
  </footer>
  </div>
</template>

<script>

  import Gauge from './components/Gauge'
  import NavSection from './components/NavSection'
  import EmployeeTable from './components/EmployeeTable'
  import MessageBoard from './components/MessageBoard'
  import GaugeCarousel from './components/GaugeCarousel'
  import AdminInfo from './components/AdminInfo'

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
      GaugeCarousel,
      AdminInfo,
    },
    created(){
      this.fetchGaugeList()
      this.fetchAdminInfo()
      this.fetchMessageList()
      this.fetchEmployeeList()
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
      async fetchEmployeeList() {
        fetch('http://localhost:3000/EmployeeList')
        .then(res => res.json())
        .then(data => this.employeeList = data)
      },
      fetchMessageList() {
        fetch('http://localhost:3000/MessageList')
        .then(res => res.json())
        .then(data => this.messageList = data)
      },
    }
  }
</script>
<style>
  html {
   background-color: #eeeeee;
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    background-color: #eeeeee;
  }
  .gauge-list-wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-top: 10px;
  }
  .section-container {
    margin: 0 1.5em;
  }
  .pb-1 {
    padding-bottom: 1em;
  }
</style>