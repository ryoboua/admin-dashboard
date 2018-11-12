<template>
  <div id="app">
    <section>
      <div class="gauge-list-wrapper">
          <Gauge v-for="gauge in gaugeList" v-bind="gauge" />
      </div>
    </section>
  </div>
</template>

<script>
import Gauge from './components/Gauge'

export default {
  name: 'App',
  data() {
    return {
      gaugeList: [],
      employeeList: [],
      messageList: [],
    }
  },
  components: {
    Gauge
  },
  created(){
    this.fetchGaugeList()
  },
  methods: {
    fetchGaugeList() {
      fetch('http://localhost:3000/GaugeList')
      .then(res => res.json())
      .then(data => this.gaugeList = data)
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
  margin-top: 60px;
}

.gauge-list-wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
