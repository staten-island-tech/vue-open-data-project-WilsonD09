<template>
  <BarChart :data="chartData" :options="chartOptions" :key="chartKey" />
</template>

<script setup>
import BarChart from '@/components/BarChart.vue'
import { onMounted, reactive, computed } from 'vue'
const fiveData = reactive([0, 0, 0, 0])
const fifteenData = reactive([0, 0, 0, 0])
async function getData5() {
  let response = await fetch('https://data.cityofnewyork.us/resource/29bw-z7pj.json?$limit=1000')
  let data = await response.json()
  return data
}
async function getData15() {
  let response = await fetch('https://data.cityofnewyork.us/resource/uvpi-gqnh.json/?$limit=1000')
  let data = await response.json()
  return data
}
async function fiveStatus() {
  let response = await getData5()
  response.forEach((item) => {
    if (item.status === 'Dead') {
      fiveData[0] += 1
    } else if (item.status === 'Poor') {
      fiveData[1] += 1
    } else if (item.status === 'Good') {
      fiveData[2] += 1
    } else if (item.status === 'Excellent') {
      fiveData[3] += 1
    }
  })
}
async function fifteenStatus() {
  let response = await getData15()
  response.forEach((item) => {
    if (item.status === 'Dead') {
      fifteenData[0] -= 1
    } else if (item.health === 'Poor') {
      fifteenData[1] -= 1
    } else if (item.health === 'Fair') {
      fifteenData[2] -= 1
    } else if (item.health === 'Good') {
      fifteenData[3] -= 1
    }
  })
}

onMounted(() => {
  fiveStatus()
  fifteenStatus()
})
console.log(fiveData)
console.log(fifteenData)
const chartData = reactive({
  labels: ['Dead', 'Poor', 'Good', 'Excellent'],
  datasets: [
    {
      label: 'Tree Census 2005',
      data: fiveData,
      backgroundColor: 'rgba(75, 192, 192, 0.6)',
    },
    {
      label: 'Tree Census 2015',
      data: fifteenData,
      backgroundColor: 'rgba(255, 99, 132, 0.6)',
    },
  ],
})
const chartOptions = reactive({
  scales: {
    y: {
      min: -1000,
      max: 1000,
    },
  },
  responsive: true,
  plugins: {
    legend: {
      position: 'top',
    },
  },
})
const chartKey = computed(() => JSON.stringify(chartData))
</script>

<style scoped></style>
