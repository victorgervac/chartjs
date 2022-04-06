<template>
  <LineChart :chartData="testData"/>
</template>

<script>
import { defineComponent } from 'vue'
import { Chart, registerables } from 'chart.js'
import { LineChart } from 'vue-chart-3'
Chart.register(...registerables)

export default defineComponent({
  name: 'LineChartExample',
  components: { LineChart },
  setup () {
    const testData = {
      labels: ['Paris', 'Nîmes', 'Toulon', 'Perpignan', 'Autre', 'USA', 'mexico'],
      datasets: [
        {
          data: [30, 40, 60, 70, 5, 10, 20],
          backgroundColor: ['#f44336', '#2196F3', '#8BC34A', '#009688', '#FBC02E', '#FFD951', '#4CAF50']
        }
      ]
    }
    return { testData }
  }
})
</script>
<style>

</style>
