<template>
  <div>
    <BarChart />
  </div>
</template>

<script setup>
import BarChart from '@/components/BarChart.vue'
import { onMounted } from 'vue'
const chartData = reactive({
  labels: [
    'PEAR, CALLERY',
    'LONDON PLANETREE',
    'MAPLE, NORWAY-CR KNG',
    'HAWTHORN, OTHER',
    'MAPLE, NORWAY',
    'HONEYLOCUST',
    'LINDEN, LITTLE LEAF',
    'UNKNOWN',
    'GINKGO',
    'GOLDENRAIN TREE',
    'DOGWOOD, FLOWERING',
    'MAPLE, SYCAMORE',
    'MAPLE, RED',
    'PLUM, PURPLELEAF',
    'ZELKOVA, JAPANESE',
    'OAK, PIN',
    'ASH, GREEN',
    'JAPANESE TREE LILAC',
    'CHERRY, OTHER',
    'MAPLE, AMUR',
    'JAPANESE PAGODA TREE',
    'KATSURA TREE',
    'OAK, NORTHERN RED',
    'Unknown Dead',
    'ELM, AMERICAN',
    'ELM, CHINESE',
    'LINDEN, SILVER',
    'OAK, WHITE',
    'LINDEN, AMERICAN',
    'OAK, SWAMP WHITE',
    'TREE OF HEAVEN',
    'DAWN REDWOOD',
    'OAK, SAWTOOTH',
    'BLACK LOCUST',
    'OAK, WILLOW',
    'HORNBEAM, AMERICAN',
    'REDBUD, EASTERN',
    'KENTUCKY COFFEETREE',
    'CHOKECHERRY, SHUBERT',
    'MAPLE, SILVER',
    'HACKBERRY',
    'BALDCYPRESS',
    'HORNBEAM, EUROPEAN',
    'POPLAR, OTHER',
    'MAPLE, HEDGE',
    'MULBERRY',
  ],
  datasets: [
    {
      data: {
        labels: treeData2005.value.map((d) => d.species),
        datasets: [
          {
            label: 'Tree Census 2005',
            data: treeData2005.value.map((d) => d.count),
            backgroundColor: 'rgba(75, 192, 192, 0.6)',
          },
          {
            label: 'Tree Census 2015',
            data: treeData2015.value.map((d) => d.count), // Negative values
            backgroundColor: 'rgba(255, 99, 132, 0.6)',
          },
        ],
      },
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
