<template>
  <div class="flex justify-around">
    <PieChart class="w-[40%]" :key="chartKey5" :data="chartData5" />
    <PieChart class="w-[40%]" :key="chartKey15" :data="chartData15" />
  </div>
</template>

<script setup>
import PieChart from '@/components/PieChart.vue'
import { reactive, onMounted, computed } from 'vue'

const fiveData = reactive([0, 0, 0, 0, 0])
const fifteenData = reactive([0, 0, 0, 0, 0])

async function getData5() {
  let response = await fetch('https://data.cityofnewyork.us/resource/29bw-z7pj.json?$limit=1000')
  let data = await response.json()
  data.forEach((item) => {
    if (item.boroname === 'Staten Island') {
      fiveData[0] += 1
    } else if (item.boroname === 'Brooklyn') {
      fiveData[1] += 1
    } else if (item.boroname === 'Queens') {
      fiveData[2] += 1
    } else if (item.boroname === 'Bronx') {
      fiveData[3] += 1
    } else if (item.boroname === 'Manhattan') {
      fiveData[4] += 1
    }
  })
}

async function getData15() {
  let response = await fetch('https://data.cityofnewyork.us/resource/uvpi-gqnh.json/?$limit=1000')
  let data = await response.json()
  data.forEach((item) => {
    if (item.boroname === 'Staten Island') {
      fifteenData[0] += 1
    } else if (item.boroname === 'Brooklyn') {
      fifteenData[1] += 1
    } else if (item.boroname === 'Queens') {
      fifteenData[2] += 1
    } else if (item.boroname === 'Bronx') {
      fifteenData[3] += 1
    } else if (item.boroname === 'Manhattan') {
      fifteenData[4] += 1
    }
  })
}

const chartData5 = reactive({
  labels: ['Staten Island', 'Brooklyn', 'Queens', 'Bronx', 'Manhattan'],
  datasets: [
    {
      data: fiveData,
      backgroundColor: ['#36A2EB', '#FF6384', '#4BC0C0', '#FFA726', '#BF53FF'],
    },
  ],
})

const chartData15 = reactive({
  labels: ['Staten Island', 'Brooklyn', 'Queens', 'Bronx', 'Manhattan'],
  datasets: [
    {
      data: fifteenData,
      backgroundColor: ['#36A2EB', '#FF6384', '#4BC0C0', '#FFA726', '#BF53FF'],
    },
  ],
})

const chartKey5 = computed(() => JSON.stringify(chartData5))
const chartKey15 = computed(() => JSON.stringify(chartData15))

onMounted(() => {
  getData5()
  getData15()
})
</script>

<style scoped></style>
