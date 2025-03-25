<template>
  <div>
    <h1>Hi</h1>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const fiveData = ref('')
const fifteenData = ref('')
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
onMounted(() => {
  getData5()
  getData15()
})
</script>

<style scoped></style>
