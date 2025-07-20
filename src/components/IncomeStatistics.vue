<template>
  <div class="card p-3 shadow-sm">
    <h6 class="mb-3 fw-bold">Income Statistics</h6>
    <canvas ref="incomeChart" style="max-height: 300px; width: 100%;"></canvas>
  </div>
</template>

<script>
import { onMounted, ref } from 'vue';
import Chart from 'chart.js/auto';

export default {
  name: 'IncomeStatistics',
  setup() {
    const incomeChart = ref(null);

    onMounted(() => {
      const ctx = incomeChart.value.getContext('2d');
      new Chart(ctx, {
        type: 'bar',
        data: {
          labels: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
          datasets: [
            {
              label: 'Online',
              data: [12, 19, 3, 5, 2, 3, 7],
              backgroundColor: '#6C63FF',
              borderRadius: 5,
              barThickness: 20
            },
            {
              label: 'Offline',
              data: [8, 11, 5, 8, 3, 7, 6],
              backgroundColor: '#63B3FF',
              borderRadius: 5,
              barThickness: 20
            }
          ]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          scales: {
            y: {
              beginAtZero: true,
              ticks: {
                stepSize: 5
              }
            }
          },
          plugins: {
            legend: {
              display: false
            }
          }
        }
      });
    });

    return { incomeChart };
  }
};
</script>

<style scoped>
.card {
  height: 350px;
  overflow: hidden;
  position: relative;
}
canvas {
  position: absolute;
  top: 40px;
  left: 0;
  right: 0;
  bottom: 0;
}
</style>
