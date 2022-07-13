<template>
  <Line
    :chart-data="data"
    :chart-options="options"
    :height="100"
  />
</template>

<script>
import { Line } from 'vue-chartjs'
import {
  Chart as ChartJS,
  Tooltip,
  LineElement,
  LinearScale,
  PointElement,
  CategoryScale,
} from 'chart.js'
import { data } from '../assets/data'

ChartJS.register(
  Tooltip,
  LineElement,
  LinearScale,
  PointElement,
  CategoryScale
)

export default {
  name: 'Chart',
  components: { Line },
  data() {
    return {
      data: {
        labels: data.map(data => data.year),
        datasets: [{
          data: data.map(data => data.userGain),
          borderColor: 'green',
          tension: 0.3,
          pointBackgroundColor: 'transparent',
          pointHoverBackgroundColor: 'green',
          pointBorderColor: 'transparent',
          pointRadius: 8,
          pointHoverRadius: 6,
        }],
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        scales: {
          x: {
            display: false
          },
          y: {
            display: false
          },
        }
      }
    }
  }
}
</script>
