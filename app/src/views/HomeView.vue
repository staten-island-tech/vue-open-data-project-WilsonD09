<template>
  <div>
    <h1>Air Quality</h1>
    <AirQuality v-for="(air, index) in airData" :key="air.name" :air="air" :id="index" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import AirQuality from '@/components/AirQuality.vue'
const airData = ref('')
async function getData() {
  let response = await fetch('https://data.cityofnewyork.us/resource/c3uy-2p5r.json')
  let data = await response.json()
  airData.value = data
}
onMounted(() => {
  getData()
})
</script>

<style scoped></style>
