<template>
    <DoughnutChart  :chartData="testData" :options="options" @chart:render="handleChartRender" />
    <button @click="shuffleData">Shuffle</button>
    <button type="button" @click="switchLegend">Swicth legends</button>
</template>
<script>
import { shuffle } from 'lodash'
import { ref, defineComponent, computed } from 'vue'
import { DoughnutChart } from 'vue-chart-3'
import { Chart, registerables } from 'chart.js'
console.log('debugger:', Chart, registerables)
Chart.register(...registerables)

export default defineComponent({
  name: 'DoughnutChartExample',
  components: { DoughnutChart },
  setup () {
    const data = ref([30, 40, 60, 70, 5, 50, 12])
    // const doughnutRef = ref()
    const toggleLegend = ref(true)

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
    const testData = computed(() => ({
      labels: ['Paris', 'Nîmes', 'Toulon', 'Perpignan', 'Autre', 'USA', 'Mexico'],
      datasets: [
        {
          data: data.value,
          backgroundColor: ['#f44336', '#2196F3', '#8BC34A', '#009688', '#FBC02E', '#FFD951', '#4CAF50']
        }
      ]
    }))
    // function addData () {
    //   dataValues.value.push(index.value)
    // }
    function shuffleData () {
      data.value = shuffle(data.value)
    }
    function switchLegend () {
      toggleLegend.value = !toggleLegend.value
    }

    return { switchLegend, testData, shuffleData, options }
  }
})
</script>
