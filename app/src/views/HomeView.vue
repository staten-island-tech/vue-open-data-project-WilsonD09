<template>
  <div>
    <h1>Air Quality</h1>
    <AirQuality v-for="(air, index) in airData" :key="air.status" :air="air" :id="index" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import AirQuality from '@/components/AirQuality.vue'
const airData = ref('')
async function getData() {
  let response = await fetch('https://data.cityofnewyork.us/resource/29bw-z7pj.json/?$limit=1000')
  let data = await response.json()
  airData.value = data
}
onMounted(() => {
  getData()
})
</script>

<style scoped></style>
