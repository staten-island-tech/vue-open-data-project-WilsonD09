<template>
  <div></div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const airData = ref('')
async function getData() {
  let response = await fetch('https://data.cityofnewyork.us/resource/dsyc-npkh.json')
  let data = await response.json()
  airData.value = data.results
}
onMounted(() => {
  getData()
})
</script>

<style scoped></style>
