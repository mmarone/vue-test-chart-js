<template>
  <div class="small">
    <line-chart :chart-data="datacollection" :options="options"></line-chart>
    <button @click="fillData()">Randomize</button>
  </div>
</template>

<script>
  import LineChart from './LineChart.js'

  export default {
    components: {
      LineChart
    },
    data () {
      return {
        datacollection: null,
        options: {
          scales: {
             yAxes: [
              {
                type: 'linear',
                display: true,
                position: 'left',
                yAxisId: 'left-y-axis'
              },
              {
                type: 'linear',
                display: true,
                position: 'right',
                yAxisId: 'right-y-axis'
              }
            ],
          }
        }
      }
    },
    mounted () {
      this.fillData()
    },
    methods: {
      fillData () {
        this.datacollection = {
          labels: [this.getRandomInt(), this.getRandomInt()],
          datasets: [
            {
              label: 'Data One',
              backgroundColor: '#f87979',
              data: [this.getRandomInt(), this.getRandomInt()],
              id: 'left-y-axis'
            }, {
              label: 'Data Two',
              backgroundColor: '#f87979',
              data: [this.getRandomInt(), this.getRandomInt()],
              id: 'right-y-axiss'
            }
          ]
        }
      },
      getRandomInt () {
        return Math.floor(Math.random() * (50 - 5 + 1)) + 5
      }
    }
  }
</script>

<style>
  .small {
    max-width: 600px;
    margin:  150px auto;
  }
</style>