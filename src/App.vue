<template>
  <div id="app">
    <nav-section v-bind=adminInfo />
    <section>
          <GaugeCarousel :gaugeList=gaugeList />
    </section>
    <!-- <section>
      <div class="gauge-list-wrapper">
          <Gauge v-for="(gauge, index) in gaugeList" :key=index v-bind=gauge />
      </div>
    </section> -->
    <section class="section-container" >
      <div class="row">
        <employee-table :employeeList=employeeList />
        <message-board :messageList=messageList />
      </div>
    </section>
  </div>
</template>

<script>

  import Gauge from './components/Gauge'
  import NavSection from './components/NavSection'
  import EmployeeTable from './components/EmployeeTable'
  import MessageBoard from './components/MessageBoard'
  import GaugeCarousel from './components/GaugeCarousel'


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
    background-color: #eeeeee;
  }

  .gauge-list-wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-top: 10px;
  }

  .section-container {
    margin: 0 2.5em;
  }
</style>