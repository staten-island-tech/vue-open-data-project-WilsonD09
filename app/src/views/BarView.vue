<template>
  <div>
    <BarChart />
  </div>
</template>

<script setup>
import BarChart from '@/components/BarChart.vue'
import { onMounted, reactive } from 'vue'
const chartData = reactive({
  labels: ['Dead', 'Poor', 'Good', 'Excellent'],
  datasets: [
    {
      label: 'Tree Census 2005',
      data: // Positive values
      backgroundColor: 'rgba(75, 192, 192, 0.6)',
    },
    {
      label: 'Tree Census 2015',
      data: // Negative values
      backgroundColor: 'rgba(255, 99, 132, 0.6)',
    },
  ],
})
async function getData5() {
  let response = await fetch('https://data.cityofnewyork.us/resource/29bw-z7pj.json?$limit=1000')
  let data = await response.json()
  fiveData.value = data
}
async function getData15() {
  let response = await fetch('https://data.cityofnewyork.us/resource/uvpi-gqnh.json/?$limit=1000')
  let data = await response.json()
  fifteenData.value = data
}

statusMap = {
  Dead: 0,
  Poor: 1,
  Good: 2,
  Excellent: 3,
}

onMounted(() => {
  getData5()
  getData15()
})
</script>

<style scoped></style>
