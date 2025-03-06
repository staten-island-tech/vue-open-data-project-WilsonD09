<template>
  <div>
    <h1>Air Quality</h1>
    <AirQuality15 v-for="(air, index) in fifteenData" :key="air.status" :air="air" :id="index" />
    <AirQuality5 v-for="(air, index) in fiveData" :key="air.status" :air="air" :id="index" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import AirQuality15 from '@/components/fifteenData.vue'
import AirQuality5 from '@/components/fiveData.vue'
const fifteenData = ref('')
async function getData15() {
  let response = await fetch('https://data.cityofnewyork.us/resource/uvpi-gqnh.json/?$limit=1000')
  let data = await response.json()
  fifteenData.value = data
}
async function getData5() {
  let response = await fetch('https://data.cityofnewyork.us/resource/29bw-z7pj.json/?$limit=1000')
  let data = await response.json()
  fifteenData.value = data
}
onMounted(() => {
  getData15()
  getData5()
})
</script>

<style scoped></style>
