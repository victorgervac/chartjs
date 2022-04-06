<template>
  <PieChart :chartData="chartData"/>
</template>

<script>
import { defineComponent, toRefs, computed } from 'vue'
import { Chart, registerables } from 'chart.js'
import { PieChart } from 'vue-chart-3'
Chart.register(...registerables)
const BACKGROUNDS = ['#f44336', '#2196F3', '#8BC34A', '#009688', '#FBC02E', '#FFD951', '#4CAF50']

export default defineComponent({
  name: 'PieChartExample',
  components: { PieChart },
  props: ['apiData'],
  setup (props) {
    const { apiData } = toRefs(props)
    const backgrounds = computed(() => {
      const colors = apiData.value.filter(c => c.backgroundColor).map((c) => c.backgroundColor)
      return colors.length > 0 ? colors : BACKGROUNDS
    })
    const chartData = computed(() => ({

      labels: apiData.value.map((c) => c.label),
      datasets: [
        {
          data: apiData.value.map(c => c.value),
          backgroundColor: backgrounds.value
        }
      ]
    }))

    return { chartData }
  }
})
</script>
<style>

</style>
