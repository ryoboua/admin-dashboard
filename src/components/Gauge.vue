<template>
      <div class="gauge-container z-depth-2 hoverable">
            <div class="radial-progress-container">
                <radial-progress-bar 
                        :completed-steps="gaugeData"
                        :startColor="mainColor"
                        :stopColor="mainColor"
                        diameter=70
                        strokeWidth=5
                        innerStrokeColor="#F3F4F4"
                        total-steps=100>
                <p>{{ gaugeData }}</p>
            </radial-progress-bar>
            </div>
            <div class="left-align info-container">
                <h6>{{ title }}</h6>
                 <div class="progress" :style="{ backgroundColor: '#F3F4F4' }" >
                    <div class="determinate" :style="{ width: `${preloaderData}%`, backgroundColor: mainColor }"></div>
                </div>
                <p> {{ increasePercentage }}% increase in 28 Days</p>
            </div>
      </div>
</template>

<script>
import RadialProgressBar from 'vue-radial-progress'

export default {
    name: 'Gauge',
    props: {
        title: {
            type: String,
            default: 'Default Name'
        },
        gaugeData: {
                type: Number,
                default: 34,
        },
        preloaderData: {
            type: Number,
            default: 20
        },
        increasePercentage: {
            type: Number,
            default: 0
        },
        mainColor: {
            type:String,
            default: 'red'
        }
    },
    components: {
        RadialProgressBar
    }
}
</script>

<style scoped>
    .gauge-container {
        padding: 1em;
        display: flex;
        flex-wrap: nowrap;
        margin: 25px;
        border-radius: 25px;
        width: 300px;
    }

    .info-container {
        flex-basis: 80%;
    }
    .radial-progress-container {
        flex-basis: 20%;
        margin: 5px 8px 0px 0px;
    }
</style>
