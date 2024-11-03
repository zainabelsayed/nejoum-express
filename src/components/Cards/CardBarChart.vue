<template>
  <div
    class="relative flex flex-col break-words bg-white w-full mb-6 shadow-lg rounded"
  >
    <div class="mb-0 px-4 py-3 bg-borders-500 text-white">
      <div class="flex flex-wrap items-center">
        <div class="relative w-full max-w-full flex-grow flex-1">
          <h2 class="capitalize mb-1 text-base">
            Arrived & Shipped Vehicles each month
          </h2>
        </div>
      </div>
    </div>
    <div class="p-4 flex-auto border-borders-500">
      <div class="relative h-350-px">
        <canvas id="bar-chart"></canvas>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import Chart from 'chart.js'
export default {
  mounted: function () {
    this.$nextTick(function () {
      const config = {
        type: 'bar',
        data: {
          labels: [
            'January',
            'February',
            'March',
            'April',
            'May',
            'June',
            'July',
          ],
          datasets: [
            {
              label: new Date().getFullYear(),
              backgroundColor: '#ed64a6',
              borderColor: '#ed64a6',
              data: [30, 78, 56, 34, 100, 45, 13],
              fill: false,
              barThickness: 15,
            },
            {
              label: new Date().getFullYear() - 1,
              fill: false,
              backgroundColor: '#4c51bf',
              borderColor: '#4c51bf',
              data: [27, 68, 86, 74, 10, 4, 87],
              barThickness: 15,
            },
          ],
        },
        options: {
          maintainAspectRatio: false,
          responsive: true,
          title: {
            display: false,
            text: 'Orders Chart',
          },
          tooltips: {
            mode: 'index',
            intersect: false,
          },
          hover: {
            mode: 'nearest',
            intersect: true,
          },
          legend: {
            labels: {
              fontColor: 'rgba(0,0,0,.4)',
            },
            align: 'end',
            position: 'bottom',
          },
          scales: {
            xAxes: [
              {
                display: true,
                scaleLabel: {
                  display: false,
                  labelString: 'Month',
                },
                gridLines: {
                  borderDash: [0],
                  borderDashOffset: [0],
                  color: 'rgba(33, 37, 41, 0.3)',
                  zeroLineColor: 'rgba(33, 37, 41, 0.3)',
                  zeroLineBorderDash: [0],
                  zeroLineBorderDashOffset: [0],
                },
              },
            ],
            yAxes: [
              {
                display: true,
                scaleLabel: {
                  display: false,
                  labelString: 'Value',
                },
                gridLines: {
                  borderDash: [0],
                  drawBorder: false,
                  borderDashOffset: [0],
                  color: 'rgba(33, 37, 41, 0.2)',
                  zeroLineColor: 'rgba(33, 37, 41, 0.15)',
                  zeroLineBorderDash: [0],
                  zeroLineBorderDashOffset: [0],
                },
              },
            ],
          },
        },
      }
      const ctx = (
        document.getElementById('bar-chart') as HTMLCanvasElement
      ).getContext('2d')
      window.myBar = new Chart(ctx, config)
    })
  },
}
</script>
