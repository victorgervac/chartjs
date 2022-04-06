<template>
    <BarChart :chartData="testData" style="width:900px, higth:400px"/>
    <button v-for="label in testData.labels" :key="label" @click="labelClicked(label)">{{label}}</button>
</template>
<script>
import { defineComponent } from 'vue'
import { BarChart } from 'vue-chart-3'
import { Chart, registerables } from 'chart.js'
Chart.register(...registerables)

export default defineComponent({
  name: 'BarChartExample',
  components: { BarChart },
  setup (props, { expose }) {
    function labelClicked (label) {
      console.log('clicked button')
    }
    const testData = {
      labels: [
        'Paris', 'Nîmes', 'Toulon', 'Perpignan', 'Autre', 'USA', 'Mexico'],
      datasets: [
        {
          data: [30, 40, 60, 70, 5, 10, 20, 80, 100],
          backgroundColor: ['#f44336', '#2196F3', '#8BC34A', '#009688', '#FBC02E', '#FFD951', '#4CAF50']
        }
      ]
    }
    expose({ labelClicked })
    return { testData }
  }
})
</script>
<style>
button{
  display: absolute;
}
</style>
