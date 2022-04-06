<template>
<div class="card">
  <DoughnutChartExample />
 </div>
 <div class="card">
  <p class="card-header"> Line Example</p>
  <hr>
  <LineChartExample />
 </div>
 <div class="card">
  <p class="card-header">Bar Example</p>
  <hr>
  <BarChartExample :labels="labels"  />
 </div>
  <div class="card">
  <p class="card-header">Pie Example</p>
  <hr>
  <PieChart :api-data="pieChartData" />
  </div>
</template>

<script>
import DoughnutChartExample from './components/DoughnutChartExample.vue'
import LineChartExample from './components/LineChartExample.vue'
import BarChartExample from './components/BarChartExample.vue'
import PieChartEx from './components/PieChartExample.vue'

export default {
  name: 'App',
  components: {
    DoughnutChartExample,
    LineChartExample,
    BarChartExample,
    PieChart: PieChartEx
  },
  data: function () {
    return {
      labels: ['Panama', 'Nîmes', 'Colombia', 'Perpignan', 'Autre', 'USA', 'Mexico'],
      pieChartData: [
        {
          label: 'panama',
          value: 13,
          backgroundColor: '#92A667'
        },
        {
          label: 'Colombia',
          value: 50,
          backgroundColor: '#48B3AC'
        }, {
          label: 'usa',
          value: 90,
          backgroundColor: '#5FA259'
        },
        {
          label: 'hondura',
          value: 4,
          backgroundColor: '#FBC02E'
        }
      ]

    }
  }
}
</script>

<style>
.card{
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  background-color: #FFFFFF;
  display:flex;
  border-radius:10px;
  padding:25px 25px 25px 25px;
  display: block;
  margin:25px;
}
.card:hover {
  box-shadow: 4px 8px 16px 4px rgba(0,0,0,0.2);
}
.card-header{
 font-size: 25px;
 color:#F44336;
 justify-content: center;
 display: flex;
}
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
