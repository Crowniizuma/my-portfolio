<template>
  <Radar :data="data" :options="options" />
</template>

<script lang="ts">

import { Radar } from 'vue-chartjs';
import {
  Chart as ChartJS,
  RadialLinearScale,
  PointElement,
  LineElement,
  Filler,
  Tooltip,
  Legend
} from 'chart.js';

export default defineComponent({
  components: {Radar},
  setup() {
    onBeforeMount(()=>{
      ChartJS.register(
        RadialLinearScale,
        PointElement,
        LineElement,
        Filler,
        Tooltip,
        Legend
      );
    });
    const data = ref({
      labels: [
        'HTML/CSS',
        'JavaScript',
        'VueJS',
        'NuxtJS',
        'Figma',
        'AdobeXD'
      ],
      datasets: [
        {
          label: '',
          backgroundColor: 'rgba(212,172,43,0.5)',
          borderColor: 'rgba(212,172,43,1)',
          pointBackgroundColor: 'rgba(212,172,43,1)',
          pointBorderColor: 'rgba(212,172,43,1)',
          pointHoverBackgroundColor: 'rgba(212,172,43,0.5)',
          pointHoverBorderColor: 'rgba(212,172,43,0.2)',
          data: [70, 50, 40, 40, 30, 20]
        }
      ]
    });

    const options = ref({
      responsive: true,
      maintainAspectRatio: true,
      plugins: {
        legend: {
          display: false,
        }
      },
      scales: {
        r: {
          min: 0,
          max: 100,
          ticks: {
                stepSize: 20
          },
          angleLines: {
            color: 'rgba(212,172,43,0.5)'
          },
          grid: {
            color: 'rgba(212,172,43,0.5)'
          }
        },
      }
    });
    return {
      data,
      options
    }
  }
})
</script>
