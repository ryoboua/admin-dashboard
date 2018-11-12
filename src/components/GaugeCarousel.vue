<template>
  <Carousel 
  :perPage=perPage()
  :paginationEnabled=true
  :paginationActiveColor=paginationActiveColor
  :paginationColor=paginationColor
  :paginationPadding=10
  >
  <Slide class="center-align" v-for="(gauge, index) in gaugeList" :key=index >
    <Gauge v-bind=gauge />
  </Slide>
</Carousel>
</template>
<script>

import Gauge from './Gauge'
import { Carousel, Slide } from 'vue-carousel';

export default {
  name: 'GaugeCarousel',
  components: {
      Gauge,
      Carousel,
      Slide,
  },
  created() {
    this.updateWindowWidth()
    window.addEventListener('resize', this.updateWindowWidth);
  },
  data() {
    return {
      paginationActiveColor: 'green',
      paginationColor: 'black',
      screenWidth: null,
      perPage(){
        if(this.screenWidth > 1200){
          return 4
        } else if (this.screenWidth > 993) {
          return 3
        } else if (this.screenWidth > 600) {
          return 2
        } else {
          return 1
        }
      }
    }
  },
  props: {
       gaugeList: {
            type: Array,
            default: () => [
                {
                title: 'I am Gauge A',
                id: 1
                },
                {
                title: 'I am Gauge B',
                id: 2
                },
                {
                title: 'I am Gauge C',
                id: 3
                },
                {
                title: 'I am Gauge D',
                id: 4
                },
                {
                title: 'I am Gauge E',
                id: 5
                }
            ]
        }
  },
  methods: {
    updateWindowWidth() {
      this.screenWidth = window.innerWidth 
    }
  },
}
</script>
<style>

</style>