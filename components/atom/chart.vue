<template>
  <div :class="$style.chartWrapper">
    <Radar :data="data" :options="options" :class="$style.chart"/>
  </div>
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
          label: 'abc',
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
            stepSize: 20,
            beginAtZero: true,
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


<style lang="scss" module>
.chartWrapper {
  width: 50%;
  padding: 5%;
  display: flex;
  justify-content: center;
  align-items: center;
  
}
</style>