<template>
    <BarChart :chartData="testData" :options="options" height="500" />
    <button v-for="label in testData.labels" :key="label" @click="labelClicked(label)">{{label}}</button>
</template>
<script>
import { defineComponent, toRefs, toRef, ref } from 'vue'
import { BarChart } from 'vue-chart-3'
import { Chart, registerables } from 'chart.js'

Chart.register(...registerables)

export default defineComponent({
  name: 'BarChartExample',
  components: { BarChart },
  props: ['labels'],
  setup (props) {
    const options = ref({
      // responsive: true,
      plugins: {
        legend: {
          position: 'bottom',
          type: 'button'

        },
        title: {
          display: true,
          text: 'DoughnutChartExample',
          position: 'top',
          color: '#F44336'
        }
      }
    })
    function labelClicked (label) {
      console.log('clicked button')
    }
    // eslint-disable-next-line no-unused-vars
    const { labels } = toRefs(props)
    // const labels = toRef(props, 'labels')
    // debugger
    const testData = {
      labels: labels.value,
      datasets: [
        {
          data: [30, 40, 60, 70, 5, 10, 20],
          backgroundColor: ['#f44336', '#2196F3', '#8BC34A', '#009688', '#FBC02E', '#FFD951', '#4CAF50']
        }
      ]
    }
    return { testData, labelClicked }
  }
})
</script>
<style>
button{
  display: absolute;
}
</style>
